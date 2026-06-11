# 01. Router 기본 Mode

Cisco Router는 작업 권한에 따라 여러 동작 Mode로 구분됩니다.
**User Mode → Privilege Mode → Global Mode** 순으로 권한이 높아집니다.

---

## User Mode

- 해당 Router에 연결된 Console, AUX, VTY(Telnet, SSH)를 사용하여 접속할 수 있다.
- 위의 방식으로 접속을 실시하게 되면 기본적으로는 User Mode로 접속이 실시된다.

```
Router>          <-- User Mode
```

- Cisco Router는 Privilege Level을 사용하여 권한을 구분한다. (Privilege Level = 0 ~ 15)
- User Mode는 Privilege Level이 1로 제한되기 때문에 해당 모드는 기본적인 상태 확인만 가능하다.

---

## Privilege Mode

- User Mode에서 상태 확인 및 관리를 실시하기 위해서는 상위 Mode로 전환을 실시해야 한다.

```
Router> enable
!
Router#          <-- Privilege Mode
```

- **상태 확인**
  - `show` : 설정한 상태 확인
  - `debug` : 실시간 상태 확인
- **저장** [RAM → NVRAM]
  - `copy`
- **삭제**
  - RAM : `reload`
  - NVRAM : `erase`
  - Flash : `delete`
- **통신 및 관리**
  - IP 네트워크 구간의 ICMP를 사용한 통신여부 확인
  - Telnet, SSH등을 사용한 원격 관리

---

## Global Mode

- Router의 RAM에 저장된 Command를 사용하여 설정을 실시하는 모드이며
  Global Mode에서 설정한 모든 command는 실시간으로 RAM에 저장된다.

```
Router# configure terminal
!
Router(config)#         <-- Global Mode
!
Router(config)# exit    : 상위 Mode로 전환
```

---

[⬆ README로 돌아가기](../README.md)
