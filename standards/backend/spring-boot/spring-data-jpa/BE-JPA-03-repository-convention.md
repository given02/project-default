# JPA Repository Convention

## Repository

- **STD-BE-JPA-030** Spring Data repository는 infrastructure 내부에 두고 application 또는 domain이 framework 타입에 직접 의존하지 않게 합니다.
- **STD-BE-JPA-031** Repository 메서드는 호출 목적과 반환 cardinality를 이름과 타입으로 드러냅니다.
- **STD-BE-JPA-032** 여러 Aggregate의 쓰기를 하나의 repository가 소유하지 않습니다.
- **STD-BE-JPA-033** 단순 조회는 derived query를 사용할 수 있지만 이름이 길어지거나 조건 의미가 불명확하면 명시적 query 구현으로 전환합니다.
