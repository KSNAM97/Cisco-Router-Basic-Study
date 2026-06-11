# 03. Router 동작원리

---

## Router 동작원리

- Router는 Layer 3에서 대표하는 장비이며 자신이 포함되지 않은 외부 네트워크와의 통신 시 사용되는 장비이다.
- 상위 Protocol로 IP를 사용하며 주소는 IP Header에 포함된 IP address를 사용한다. (10진수 32bit의 주소 체계)
- Router는 데이터가 입력되면 Layer 3 Header에 포함된 IP 주소를 근거로 Routing Table을 참조하여 Next-hop으로 전송
- Router는 Routing Table에 등록되지 않은 네트워크 정보는 Drop을 실시한다.
- Router는 전송과정에서의 통신은 책임지지 않는다. (Next-hop까지만)
- Router는 직접 연결된 Local 네트워크 정보는 가장 신뢰하여 Connected로 라우팅을 학습 실시한다. (Routing Table 등록)
- Router는 직접 연결되지 않은 원격지 네트워크 정보는 Static, Dynamic Routing Protocol을 사용하여 라우팅을 학습 실시

---

## 라우팅 학습

- 라우팅 학습이란 원격지 네트워크 정보를 학습하는 과정
- 라우팅 학습을 실시하기 위해서는 Routing Protocol 안에 반드시 Next-hop이 포함되어야 한다.

---

## 참고 명령어

### 스위치 기본 게이트웨이 설정 순서

```
en
conf t
int fa0/0
ip add 192.168.1.254 255.255.255.0
no sh
ctrl+z
wr
```

### ARP Table 확인

```
en
sh arp
```

### CLI에서 ping 응답 표시

- `.` (Dot) : 실패 (응답 X)
- `!` (Exclamation) : 성공 (응답 O)

---

[⬆ README로 돌아가기](../README.md)
