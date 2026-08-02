# JPA Entity Lifecycle Convention

## 기준

- **STD-BE-JPA-020** Entity callback에 외부 호출, repository 조회와 복잡한 비즈니스 규칙을 두지 않습니다.
- **STD-BE-JPA-021** 영속화 시점에 결정되는 ID에 domain 생성 규칙이 의존하지 않게 합니다.
