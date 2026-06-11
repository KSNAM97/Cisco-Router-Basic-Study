# 02. RAM & NVRAM

- Router는 RAM을 사용하는 즉시 저장된 모든 Command를 RAM에 저장과 실시되며
  해당 Router의 RAM에 저장된 Command만으로 동작을 실시한다.

---

## RAM vs NVRAM 비교

| 구분 | RAM | NVRAM |
| --- | --- | --- |
| 특징 | 휘발성 메모리 | 비휘발성 메모리 |
| 확인 | `show running-config` | `show startup-config` |
| 저장 | 실시간 저장 [Enter] | `copy running-config startup-config` |
| 삭제 | `reload` | `erase startup-config` |

---

## 명령어 정리

```
Router# show running-config                      : RAM 설정 확인
Router# show startup-config                      : NVRAM 설정 확인
Router# copy running-config startup-config       : RAM → NVRAM 저장
Router# erase startup-config                     : NVRAM 설정 삭제
Router# reload                                   : 재부팅 (RAM 초기화)
```

> 💡 RAM은 휘발성이므로 재부팅(reload) 시 저장하지 않은 설정은 사라진다.
> 영구 보존하려면 반드시 `copy running-config startup-config`로 NVRAM에 저장해야 한다.

---

[⬆ README로 돌아가기](../README.md)
