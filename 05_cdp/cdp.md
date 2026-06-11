# 05. CDP (Cisco Discovery Protocol)

- 해당 Router, Switch에 직접 연결된 장비의 기본적인 정보를 확인할 수 있다.

---

## CDP를 사용하기 위한 조건

- Cisco 장비 연결 시에만 사용할 수 있다.
- Layer 2가 활성화 상태일 경우 확인이 가능하다.
- 직접 연결된 장비의 정보만 확인이 가능하다.

---

## 확인 가능한 정보

- CDP Message는 60초 주기로 전송하며 180초간 유지된다. [`show cdp`]

| 항목 | 설명 |
| --- | --- |
| Version | IOS Version |
| Device ID | 인접한 장비의 Hostname |
| Local Interface | 해당 장비의 Interface |
| Port ID | 인접한 장비의 Interface |
| Platform | 인접장비의 Platform |
| Capability | Router / Switch |
| Next-hop IP | 인접한 Interface의 IP |

---

## 명령어

```
RTX# show cdp
RTX# show cdp neighbor              : 인접 장비의 Interface를 확인
RTX# show cdp neighbor detail

RTX(config)# no cdp run             : CDP 기능 정지
RTX(config)# cdp timer <sec>        : CDP Message 교환 주기 설정
RTX(config)# cdp holdtime <sec>     : holdtime 설정
```

---

[⬆ README로 돌아가기](../README.md)
