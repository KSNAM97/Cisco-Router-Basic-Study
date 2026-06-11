# 04. Twisted-Pair Cable

UTP Cable은 연결하는 장비의 종류에 따라 사용하는 결선 방식이 다르다.

---

## UTP Straight-Through Cable (Direct)

- 다른 종류의 장비 연결에 사용되는 Cable

```
                Fa              Fa
 EX)      PC -------------- Switch

                Fa              Fa
 EX) Switch -------------- Router
```

### 핀 배열 (Switch ─ Router)

```
        Switch              Router
        주백 ──────────────── 주백
        주   ──────────────── 주
        녹백 ──────────────── 녹백
        파   ──────────────── 파
        파백 ──────────────── 파백
        녹   ──────────────── 녹
        갈백 ──────────────── 갈백
        갈   ──────────────── 갈
```

---

## UTP Crossover Cable

- 같은 종류의 장비 연결에 사용되는 Cable

```
                Fa              Fa
 EX)      PC -------------- PC

                Fa              Fa
 EX) Switch -------------- Switch

                Fa              Fa
 EX)     Hub -------------- Hub

                Fa              Fa
 EX) Router -------------- Router

                Fa              Fa
 EX)      PC -------------- Router
```

### 핀 배열 (Switch ─ Switch)

```
        Switch              Switch
        주백 ──────────────── 녹백
        주   ──────────────── 녹
        녹백 ──────────────── 주백
        파   ──────────────── 파
        파백 ──────────────── 파백
        녹   ──────────────── 주
        갈백 ──────────────── 갈백
        갈   ──────────────── 갈
```

---

## UTP Roll-over Cable (Console Cable)

- Router, Switch의 Console Port에 접속 시 사용되는 Cable

```
                              Con
 EX)      PC -------------- Router

                              Con
 EX)      PC -------------- Switch
```

### 핀 배열 (PC ─ Switch)

```
          PC                Switch
        주백 ──────────────── 갈
        주   ──────────────── 갈백
        녹백 ──────────────── 녹
        파   ──────────────── 파백
        파백 ──────────────── 파
        녹   ──────────────── 녹백
        갈백 ──────────────── 주
        갈   ──────────────── 주백
```

---

[⬆ README로 돌아가기](../README.md)
