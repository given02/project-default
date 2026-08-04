# PostgreSQL Schema Convention

## 식별자와 Type

- **STD-DB-PG-010** 식별자는 따옴표 없이 사용할 수 있는 lowercase `snake_case`로 작성합니다.
- **STD-DB-PG-011** 자동 증가 식별자가 필요하면 `serial` pseudo-type보다 SQL identity column을 사용합니다.
- **STD-DB-PG-012** UUID를 저장하면 문자열 type이 아니라 PostgreSQL `uuid` type을 사용합니다.
- **STD-DB-PG-013** 특정 시점은 `timestamp with time zone`을 사용하고 날짜 또는 지역의 벽시계 시간이 의미인 경우에만 `date`, `time` 또는 `timestamp without time zone`을 사용합니다.
- **STD-DB-PG-014** 금액과 정확한 소수 계산에는 precision과 scale이 명확한 `numeric`을 사용합니다.
- **STD-DB-PG-015** 문자열 길이가 실제 business constraint가 아니면 임의 길이의 `varchar(n)`으로 제한하지 않고 `text`를 사용합니다.
- **STD-DB-PG-016** 비정형 구조라는 이유만으로 `jsonb`를 사용하지 않으며 안정적인 조회, constraint와 관계가 필요한 값은 column과 table로 모델링합니다.
- **STD-DB-PG-017** `jsonb`를 사용하면 저장 구조, runtime validation, 변경 호환성과 필요한 index를 Requirement의 Database 설계에 정의합니다.
- **STD-DB-PG-018** array type은 값의 독립적 identity, 관계와 자주 변경되는 요소가 필요하지 않은 경우에만 사용합니다.
