# JPA Repository Convention

## Repository

- **STD-BE-JPA-030** Spring Data repository는 infrastructure 내부에 두고 application 또는 domain이 framework 타입에 직접 의존하지 않게 합니다.
- **STD-BE-JPA-031** Repository 메서드는 호출 목적과 반환 cardinality를 이름과 타입으로 드러냅니다.
- **STD-BE-JPA-032** 여러 Aggregate의 쓰기를 하나의 repository가 소유하지 않습니다.
- **STD-BE-JPA-033** 단순 조회는 Spring Data JPA의 기본 repository method와 읽기 쉬운 derived query로 구현합니다. method 이름이 길어지거나 조건 의미가 불명확해지면 **STD-BE-JPA-047**의 QueryDSL 구현으로 전환합니다.
- **STD-BE-JPA-034** Spring Data JPA repository method에 JPQL 또는 native SQL을 문자열로 선언하는 `@Query` annotation을 사용하지 않습니다. 복잡한 조회, bulk 변경과 Database 전용 조회는 infrastructure의 명시적인 구현으로 분리합니다.
