# Database Schema Convention

## Source Of Truth와 명명

- **STD-DB-010** 제품 의미, business invariant와 데이터 소유권은 Requirement가 소유하고 실행 가능한 schema는 적용된 versioned migration이 소유합니다.
- **STD-DB-011** Requirement의 Database 설계와 migration이 충돌하면 같은 작업에서 원인을 확인하고 정렬합니다.
- **STD-DB-012** ORM entity, API model과 화면 편의를 Database 의미로 재정의하지 않습니다.
- **STD-DB-013** table과 column은 lowercase `snake_case`를 사용합니다.
- **STD-DB-014** table 이름의 단수 또는 복수 방식은 프로젝트 전체에서 하나로 통일합니다.
- **STD-DB-015** 예약어, 따옴표가 필요한 식별자와 의미 없는 `data`, `value`, `info`, `flag` 이름을 사용하지 않습니다.

## Object 이름

| Object            | 형식                            |
| ----------------- | ------------------------------- |
| Primary key       | `pk_<table>`                    |
| Foreign key       | `fk_<table>_<referenced_table>` |
| Unique constraint | `uk_<table>_<meaning>`          |
| Check constraint  | `ck_<table>_<rule>`             |
| 일반 index        | `idx_<table>_<purpose>`         |

- **STD-DB-016** Database object 이름은 위 형식을 사용하고 복합 object는 모든 column을 나열하기보다 규칙이나 조회 목적을 드러냅니다.

## Table과 Column

- **STD-DB-017** 하나의 table은 하나의 명확한 데이터 책임과 소유 Aggregate 또는 component를 가집니다.
- **STD-DB-018** 계산으로 안정적으로 도출할 값을 중복 저장하지 않으며 성능상 저장하면 갱신 책임과 정합성 복구 방법을 Requirement에 정의합니다.
- **STD-DB-019** type은 저장 크기보다 값의 의미, 범위, 정밀도와 연산을 안전하게 표현하도록 선택합니다.
