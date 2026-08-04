# PostgreSQL Schema Feature Convention

## Constraint와 기능

- **STD-DB-PG-020** case-insensitive uniqueness는 application의 소문자 변환만으로 보장하지 않고 정규화 column, expression index 또는 검토된 PostgreSQL 기능으로 Database에서 보호합니다.
- **STD-DB-PG-021** soft delete 상태를 제외한 uniqueness가 필요하면 조건을 명확히 표현한 partial unique index를 사용합니다.
- **STD-DB-PG-022** sequence와 identity의 실제 범위는 예상 규모에 맞추고 application이 다음 값을 추측하지 않게 합니다.
- **STD-DB-PG-023** extension은 migration으로 설치하고 필요성, 권한, 지원 환경과 제거 영향을 검토합니다.
- **STD-DB-PG-024** Database function, trigger와 generated column은 application에서 보이지 않는 business rule을 만들지 않으며 사용하는 경우 책임과 테스트를 Requirement에 기록합니다.
- **STD-DB-PG-025** schema search path에 암묵적으로 의존하지 않고 application과 migration의 대상 schema를 일관되게 구성합니다.
