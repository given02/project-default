# Backend Transaction Convention

## 기준

- **STD-BE-060** transaction boundary는 하나의 use case를 조정하는 application 계층에 둡니다.
- **STD-BE-061** Database transaction 안에서 불필요한 외부 네트워크 호출을 수행하지 않습니다.
- **STD-BE-062** lock, optimistic concurrency와 retry를 사용하면 충돌 조건, 최대 범위, 재시도 가능 오류와 idempotency를 함께 정의합니다.
- **STD-BE-063** 여러 저장소나 외부 시스템 사이의 일관성은 원자적 transaction으로 위장하지 않고 outbox, saga 또는 보상 같은 명시적 전략을 Requirement에 정의합니다.
