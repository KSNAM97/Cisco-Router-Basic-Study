# Cisco Router Study

![Cisco](https://img.shields.io/badge/Cisco-1BA0D7?style=flat&logo=cisco&logoColor=white)
![Router](https://img.shields.io/badge/Router-005073?style=flat)
![GNS3](https://img.shields.io/badge/GNS3-00979D?style=flat)
![License](https://img.shields.io/badge/License-MIT-green.svg)

**Cisco Router 기초 (Mode / Interface / CDP / Password / Routing)**

---

Cisco IOS 기반 **Router 기초 동작 원리와 설정**을 정리한 학습 저장소입니다.
Router의 **운영 Mode, RAM/NVRAM 저장 구조, Interface(Ethernet/Serial/Loopback) 설정,
CDP, Cable 종류, Password, Enable Secret** 까지 단계별로 다룹니다.
**CCNA** 학습 및 네트워크 입문 실습용으로 활용할 수 있습니다.

---

| 항목 | 내용 |
| --- | --- |
| 대상 장비 | Cisco Router (IOS) |
| 핵심 주제 | Router Mode, RAM/NVRAM, Interface, CDP, Cable, Password |
| 실습 환경 | GNS3 / Cisco Packet Tracer |
| 주요 명령어 | enable, configure terminal, ip address, no shutdown, encapsulation, clock rate |

---

```
cisco-router-study/
├── 01_router-modes/          # Router 기본 Mode (User/Privilege/Global)
├── 02_ram-nvram/             # RAM, NVRAM 저장/삭제
├── 03_router-operation/      # Router 동작원리 & 라우팅 학습
├── 04_cable/                 # Twisted-Pair Cable
├── 05_cdp/                   # CDP (Cisco Discovery Protocol)
├── 06_router-interface/      # Ethernet / Serial / Loopback Interface
├── 07_router-password/       # Console / VTY / AUX Password
├── 08_enable-secret/         # Enable Secret / Enable Password
├── LICENSE
└── README.md
```

---

## 📚 챕터 (Chapters)

| # | 챕터 | 내용 |
| --- | --- | --- |
| 01 | [Router 기본 Mode](./01_router-modes/router-modes.md) | User / Privilege / Global Mode, Privilege Level |
| 02 | [RAM & NVRAM](./02_ram-nvram/ram-nvram.md) | running-config, startup-config, 저장/삭제 |
| 03 | [Router 동작원리](./03_router-operation/router-operation.md) | Layer 3 동작, Routing Table, Next-hop, 라우팅 학습 |
| 04 | [Twisted-Pair Cable](./04_cable/cable.md) | Straight-Through / Crossover / Roll-over |
| 05 | [CDP](./05_cdp/cdp.md) | Cisco Discovery Protocol, 인접 장비 정보 확인 |
| 06 | [Router Interface](./06_router-interface/router-interface.md) | Ethernet / Serial / Loopback Interface |
| 07 | [Router Password](./07_router-password/router-password.md) | Console / VTY / AUX Password |
| 08 | [Enable Secret / Password](./08_enable-secret/enable-secret.md) | enable secret(MD5) / enable password(Text) |

---

## 핵심 개념 요약

- **User Mode** : 기본 진입 모드, Privilege Level 1, 기본 상태 확인만 가능
- **Privilege Mode** : `enable` 진입, show/debug/copy/reload 등 관리 명령 가능
- **Global Mode** : `configure terminal` 진입, 설정이 실시간으로 RAM에 저장
- **RAM** : 휘발성 메모리, running-config
- **NVRAM** : 비휘발성 메모리, startup-config
- **Routed/Interface** : Ethernet(LAN), Serial(WAN), Loopback(논리)
- **CDP** : Cisco 전용 L2 인접 장비 탐색 프로토콜

---

## License

[MIT License](./LICENSE)
