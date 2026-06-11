# 07. Router Password

---

## Router의 접속 방식

- **Console 접속** : 관리자가 Console Cable을 사용하여 Router의 Console Port로 직접 접속하는 방식
- **AUX 접속** : Modem을 사용해서 원격으로 접속하는 방식
- **VTY 접속** : 인터넷 같은 매개체를 통해 Telnet(TCP 23), SSH(TCP 22)를 사용해서 원격으로 접속하는 방식

> Router의 Password는 접속방식에 따라 Password를 설정 및 권한에 따라 Password를 설정이 가능하다.

---

## Console Password

- 관리자가 PC를 Serial로 Router의 Console Port에 연결하여 직접 접속 시 Password를 설정하여 보안을 강화
- Console은 물리적인 Port이기 때문에 한명의 사용자만 접속할 수 있다. [관리자만 접속 가능]
- Password는 대/소문자를 구분하며 공백도 하나의 Password로 인식된다. [단, 중간 공백만 인식한다.]
- Password 설정은 대문자, 소문자, 숫자, 특수 문자의 조합으로 7자 이상 사용하는것을 권장하며
  안전하게 보안 시에는 13자 이상 사용하는것이 좋다.

```
Router(config)# line console 0
Router(config-line)# password WORD
Router(config-line)# login
```

---

## VTY Password

- Internet의 매개체를 사용한 원격 접속하는 Protocol인
  Telnet(TCP 23), SSH(TCP 22)을 사용하여 접속 시 Password를 설정하여 보안을 강화
- VTY는 논리적인 Port이기 때문에 다수의 사용자가 접속이 가능하다.
  (Router는 5개의 Port를 지원하며 Switch는 16개의 Port를 지원한다.)
- Password는 대/소문자를 구분하며 공백도 하나의 Password로 인식된다. [단, 중간 공백만 인식한다.]
- Password 설정은 7자 이상 권장, 보안 시 13자 이상 권장.

```
Router(config)# line vty 0 4
Router(config-line)# password WORD
Router(config-line)# login
```

---

## AUX Password

- Modem을 사용하여 원격접속 시 Password를 설정하여 보안을 강화
- Password는 대/소문자를 구분하며 공백도 하나의 Password로 인식된다. [단, 중간 공백만 인식한다.]
- Password 설정은 7자 이상 권장, 보안 시 13자 이상 권장.

```
Router(config)# line aux 0
Router(config-line)# password WORD
Router(config-line)# login
```

---

[⬆ README로 돌아가기](../README.md)
