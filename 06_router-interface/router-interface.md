# 06. Router Interface

- Router의 Interface는 크게 LAN 구간을 연결하는 Ethernet Interface와
  WAN 구간을 연결하는 Serial Interface, 논리적 Interface인 Loopback Interface로 구분이 가능하다.
- Ethernet Interface, Serial Interface는 물리적 Interface이며 Loopback Interface는 논리적 Interface이다.
- Cisco Router에서 물리적 Interface는 [Ethernet, Serial] 기본적으로
  Layer 1이 비활성화 상태(Shutdown)이기 때문에 수동으로 활성화 상태로 전환해야 한다.

---

## 토폴로지

```
                  192.168.12.0/24                  192.168.23.0/24
            S1/0              S1/1   S1/0              S1/1
        R1 -------------------- R2 -------------------- R3
         |                       |                       |
       Fa0/0                   Fa0/0                   Fa0/0
         |                       |                       |
        SW1                     SW2                     SW3
   192.168.1.0/24          192.168.2.0/24          192.168.3.0/24
```

---

## Ethernet Interface

- LAN 구간을 연결하는 Interface이며 IEEE에서 제정한 LAN 관련 표준 Protocol이기 때문에
  접속방식, 전송속도, 대역폭등이 표준으로 제정되어 있기 때문에
  Layer 1만 활성화하면 Layer 2부터는 기본적으로 동작 및 통신이 가능하다.

### R1 설정

```
Router# conf t
!
Router(config)# hostname R1
!
R1(config)# interface fastethernet 0/0
R1(config-if)# no shutdown                              : Layer 1 활성화 상태로 전환
R1(config-if)# ip address 192.168.1.254 255.255.255.0   : Layer 3 주소 할당 (Layer 2는 표준이므로 설정 생략)
```

### 상태 확인

```
R1# show ip route        : Routing Table 확인
C    192.168.1.0/24 is directly connected, FastEthernet0/0

R1# ping 192.168.1.1     : PC <----- G/W
R1# ping 192.168.1.2     : PC <----- G/W
R1# ping 192.168.1.3     : PC <----- G/W
PC> ping 192.168.1.254   : PC -----> G/W

R1# show arp             : ARP Table 확인
```

```
Protocol  Address         Age(min)  Hardware Addr     Type   Interface
Internet  192.168.1.1        1       000A.F326.2AD5   ARPA   FastEthernet0/0
Internet  192.168.1.2        0       00D0.BA4B.B3A2   ARPA   FastEthernet0/0
Internet  192.168.1.3        0       000C.858D.7C45   ARPA   FastEthernet0/0
Internet  192.168.1.254      -       00D0.BC20.3901   ARPA   FastEthernet0/0
```

```
R1# show interface fastethernet 0/0
FastEthernet0/0 is up, line protocol is up (connected)
  Hardware is Lance, address is 00d0.bc20.3901 (bia 00d0.bc20.3901)
  Internet address is 192.168.1.254/24
  MTU 1500 bytes, BW 100000 Kbit, DLY 100 usec,
     reliability 255/255, txload 1/255, rxload 1/255
```

### R2 설정

```
Router# conf t
!
Router(config)# hostname R2
!
R2(config)# interface fastethernet 0/0
R2(config-if)# no shutdown
R2(config-if)# ip address 192.168.2.254 255.255.255.0

R2# show ip route
R2# show arp
R2# show interface fastethernet 0/0
R2# show running-config
R2# ping 192.168.2.1
R2# ping 192.168.2.2
```

### R3 설정

```
Router# conf t
!
Router(config)# hostname R3
!
R3(config)# interface fastethernet 0/0
R3(config-if)# no shutdown
R3(config-if)# ip address 192.168.3.254 255.255.255.0

R3# show ip route
R3# show arp
R3# show interface fastethernet 0/0
R3# show running-config
R3# ping 192.168.3.1
R3# ping 192.168.3.2
```

---

## Serial Interface

- WAN 구간 통신에 사용되는 Interface이며
  Ethernet과는 달리 Layer 2 Protocol과 전송속도, 대역폭을 설정해주어야 한다.
- WAN 구간에서 Layer 2가 활성화 되기 위해서는 Layer 2 Protocol을 설정해야 하며
  DCE에서 Clock Rate 설정을 실시해야 한다.

### R1 [DTE]

```
R1(config)# interface serial 1/0
R1(config-if)# no shutdown
R1(config-if)# encapsulation hdlc
R1(config-if)# bandwidth 64
R1(config-if)# ip address 192.168.12.1 255.255.255.0
```

### R2 [DCE]

```
R2(config)# interface serial 1/1
R2(config-if)# no shutdown                              : Layer 1 활성화 상태로 전환 (shutdown은 비활성화)
R2(config-if)# encapsulation hdlc                       : Layer 2 Protocol 설정 (Cisco Serial 기본 HDLC)
R2(config-if)# bandwidth 64                             : 대역폭 설정 [단위 : Kbps]
R2(config-if)# clock rate 64000                         : 대역폭의 물리적인 속도 설정 [단위 : bps]
R2(config-if)# ip address 192.168.12.2 255.255.255.0    : Layer 3 주소 할당
!
R2(config)# interface serial 1/0
R2(config-if)# no shutdown
R2(config-if)# encapsulation hdlc
R2(config-if)# bandwidth 64
R2(config-if)# clock rate 64000
R2(config-if)# ip address 192.168.23.2 255.255.255.0
```

### R3 [DTE]

```
R3(config)# interface serial 1/1
R3(config-if)# no shutdown
R3(config-if)# encapsulation hdlc
R3(config-if)# bandwidth 64
R3(config-if)# ip address 192.168.23.3 255.255.255.0
```

### 상태 확인

```
R1# show ip route
R1# show interface serial 1/0
R1# show controller serial 1/0
R1# show ip interface brief
R1# ping 192.168.12.2

R2# show ip route
R2# show interface serial 1/0     : Serial Interface 기본 상태 확인
R2# show interface serial 1/1     : Serial Interface 기본 상태 확인
R2# show controller serial 1/0    : Serial Interface의 DCE, DTE, Clock rate 확인
R2# show controller serial 1/1    : Serial Interface의 DCE, DTE, Clock rate 확인
R2# show ip interface brief       : Interface의 간략정보 확인
R2# ping 192.168.12.1             : R1 Next-hop 통신 검증
R2# ping 192.168.23.3             : R3 Next-hop 통신 검증

R3# show ip route
R3# show interface serial 1/1
R3# show controller serial 1/1
R3# show ip interface brief
R3# ping 192.168.23.2
```

---

## Loopback Interface

- Loopback Interface는 물리적으로 존재하는 Port가 존재하지 않는 논리적인 Port이다.
- Test 또는 가상으로 네트워크를 추가해 사용할 수 있는 Interface이다.
- Loopback Interface는 논리적 Interface이기 때문에 Layer 1, Layer 2가 활성화 상태이므로
  IP 주소만 설정을 실시하게 되면 통신이 가능하다.
  (단 `shutdown` command를 사용하여 비활성화 상태로 전환도 가능하다.)

```
Router(config)# interface loopback <0-2147483647>
Router(config-if)# ip address [A.B.C.D] [Subnetmask]
```

---

## show ip interface brief 상태 판독

```
R1# show ip interface brief
Interface      IP-Address    OK? Method  Status                  Protocol

Serial1/0      unassigned    YES unset   administratively down   down    : 해당 장비 interface가 Shutdown 상태
Serial1/1      unassigned    YES unset   down                    down    : 인접 장비 Interface 상태가 shutdown인 경우
Serial1/2      unassigned    YES unset   up                      down    : Encapsulation type이 다르거나 Clock 설정 누락
Serial1/3      unassigned    YES unset   up                      up      : Layer 1, Layer 2 활성화 상태
```

---

[⬆ README로 돌아가기](../README.md)
