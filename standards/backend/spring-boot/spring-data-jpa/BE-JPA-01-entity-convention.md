# JPA Entity Convention

## 기준

- **STD-BE-JPA-010** JPA entity는 persistence model이며 API 요청·응답 타입으로 사용하지 않습니다.
- **STD-BE-JPA-011** Entity의 table, column, key, nullable과 constraint mapping은 Customs의 database schema와 migration에 일치시킵니다.
- **STD-BE-JPA-012** 기본 생성자는 JPA에 필요한 최소 접근 수준으로 제한합니다.
- **STD-BE-JPA-013** Entity 상태는 public setter를 일괄 제공하지 않고 의미 있는 생성 및 변경 메서드를 통해 바꿉니다.
- **STD-BE-JPA-014** `equals`와 `hashCode`는 영속화 전후에 변하는 값이나 지연 로딩 연관관계 전체에 의존하지 않습니다.
- **STD-BE-JPA-015** `toString`에 지연 로딩 연관관계와 민감정보를 포함하지 않습니다.
- **STD-BE-JPA-016** 연관관계는 기본적으로 지연 로딩을 사용하고 필요한 조회에서 fetch 전략을 명시합니다.
- **STD-BE-JPA-017** 양방향 연관관계는 양쪽 탐색이 실제로 필요하고 일관성 관리 책임이 명확할 때만 사용합니다.
- **STD-BE-JPA-018** Cascade와 orphan removal은 같은 Aggregate 소유권과 생명주기를 가질 때만 사용합니다.
- **STD-BE-JPA-019** Enum은 ordinal로 저장하지 않고 schema의 허용 값 및 변경 전략과 일치하는 안정적인 표현을 사용합니다.
