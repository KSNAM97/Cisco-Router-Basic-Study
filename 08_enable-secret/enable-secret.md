# 08. Enable Secret & Enable Password

- 해당 Router의 Console, AUX, VTY 등을 사용하여 접속을 실시하게 되면 우선 User Mode로 접속이 실시된다.
  하지만 User Mode에서는 해당 장비의 기본적인 상태 확인만 가능하기 때문에
  관리를 실시하기 위해서는 상위 Mode인 Privilege Mode로 전환을 실시해야 한다.
- Privilege Mode로 전환하기 위해서 `enable` command를 입력하게 되면 password를 묻는다.

---

## 명령어

```
Router(config)# enable secret WORD       : 설정한 Password를 MD5 HASH 알고리즘으로 암호화
Router(config)# enable password WORD     : 설정한 Password를 Text 평문으로 저장
```

---

## 비교

| 구분 | enable secret | enable password |
| --- | --- | --- |
| 저장 방식 | MD5 HASH 암호화 | Text 평문 |
| 보안성 | 높음 (권장) | 낮음 |

> ⚠️ Enable Secret, Enable Password를 동일한 Password로 설정할 수 없다.
> 두 가지가 모두 설정된 경우 **Enable Secret이 우선 적용**된다.

---

[⬆ README로 돌아가기](../README.md)
