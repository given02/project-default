# Database Convention

- Owner: Backend Developer
- Purpose: 프로젝트의 물리 데이터베이스 schema, 명명, 타입, key, constraint, index와 보안 규칙을 정의합니다.
- Audience: Backend Developer와 데이터베이스 변경 검토자
- Dependencies: `../../documents/architecture/domain-model.md`, `../../documents/product/business-rule.md`, `project-environment.md`
- Next Reading: `database-schema-definition.md`

## 경계와 Source Of Truth

- 제품 의미, business invariant와 데이터 소유권은 Architect가 소유하는 공유 문서를 따릅니다.
- 이 문서는 물리 데이터베이스 설계 규칙의 source of truth입니다.
- 프로젝트의 실제 테이블 정의는 `database-schema-definition.md`에서 관리합니다.
- 실행 가능한 schema의 source of truth는 적용된 versioned migration입니다.
- 문서와 migration이 충돌하면 원인을 확인하고 같은 작업에서 명시적으로 정렬합니다.
- ORM entity, API model 또는 특정 화면의 편의를 데이터베이스 의미로 재정의하지 않습니다.

## 프로젝트 결정

프로젝트 초기화 시 다음 항목을 확정하고 적용하지 않는 항목은 `해당 없음`과 이유를 기록합니다.

| 항목 | 결정 | Source Of Truth |
| --- | --- | --- |
| Database 및 버전 | {{DATABASE_AND_VERSION}} | `project-environment.md` |
| 기본 schema 또는 namespace | {{DEFAULT_SCHEMA}} | {{CONFIG_OR_MIGRATION}} |
| Identifier 전략 | {{IDENTIFIER_STRATEGY}} | 이 문서와 migration |
| 날짜·시간 및 timezone | {{DATE_TIME_AND_TIMEZONE_POLICY}} | 이 문서 |
| 문자 정렬 및 대소문자 | {{COLLATION_AND_CASE_POLICY}} | DB 설정과 이 문서 |
| Enum 저장 전략 | {{ENUM_STORAGE_POLICY}} | 이 문서 |
| 암호화 전략 | {{ENCRYPTION_POLICY}} | 보안 설정과 ADR |
| 예상 데이터 규모 | {{EXPECTED_DATA_SCALE}} | 요구사항 또는 용량 계획 |

## 명명

- 테이블과 컬럼은 `snake_case`를 사용합니다.
- 테이블 이름은 프로젝트에서 단수 또는 복수 중 하나를 선택하고 일관되게 유지합니다.
- 약어는 `../../documents/glossary/glossary.md`에 정의된 코드 표현을 사용합니다.
- 이름만으로 의미를 알 수 없는 `data`, `value`, `info`, `flag` 같은 범용 이름을 피합니다.
- 예약어와 따옴표가 필요한 식별자를 사용하지 않습니다.
- 식별자 길이 제한 때문에 이름이 잘릴 수 있으면 충돌 없는 축약 규칙을 정합니다.

### Object 이름

| Object | 형식 | 예시 |
| --- | --- | --- |
| Primary key | `pk_<table>` | `pk_orders` |
| Foreign key | `fk_<table>_<referenced_table>` | `fk_orders_users` |
| Unique constraint | `uk_<table>_<meaningful_columns>` | `uk_users_email` |
| Check constraint | `ck_<table>_<rule>` | `ck_orders_status` |
| 일반 index | `idx_<table>_<purpose_or_columns>` | `idx_orders_user_created` |

복합 object 이름은 전체 컬럼을 기계적으로 나열하기보다 충돌하지 않는 범위에서 조회 또는 규칙의 의미를 드러냅니다.

## 테이블

- 하나의 테이블은 하나의 명확한 데이터 책임을 가집니다.
- 테이블이 소유하는 Aggregate 또는 데이터 소유 컴포넌트를 명시합니다.
- 다대다 관계는 관계 자체의 속성, 생명주기와 중복 방지 constraint를 검토합니다.
- 공통 파일, 코드 또는 이력 테이블을 사용할 때 도메인별 연결 테이블과 소유권을 명시합니다.
- 계산으로 안정적으로 도출할 수 있는 값은 중복 저장하지 않습니다. 성능을 위해 저장하면 갱신 책임과 정합성 복구 방법을 문서화합니다.
- 예상 row 수, 증가율, 보존 기간과 주요 접근 패턴을 설계 근거에 포함합니다.

## Column과 데이터 타입

- 가장 작은 타입이 아니라 의미와 예상 범위를 안전하게 표현하는 타입을 선택합니다.
- Identifier 전략은 sequence/identity, UUID 등에서 프로젝트 전체 기준을 정하고 예외를 기록합니다.
- Foreign key 컬럼은 참조 대상 key와 호환되는 타입을 사용합니다.
- 금액과 정밀 계산은 부동소수점 대신 명시적인 precision과 scale을 가진 decimal/numeric 타입을 사용합니다.
- 날짜·시간은 의미가 날짜인지, 로컬 시간인지, 특정 시점인지 구분합니다.
- 특정 시점은 timezone 정책과 함께 저장하며 API 계약의 시간 표현과 일치시킵니다.
- boolean 기본값은 DB가 이해하는 `true` 또는 `false`로 표현하고 `Y`, `N`, `0`, `1`을 혼용하지 않습니다.
- 상태 값은 자유 문자열로 방치하지 않고 enum, lookup table 또는 check constraint 중 하나로 유효 범위를 보장합니다.
- 대용량 binary는 기본적으로 object storage에 저장하고 DB에는 식별자와 metadata를 저장합니다. 예외는 크기와 운영 근거를 기록합니다.

## NULL과 Default

- `NULL`은 값이 아직 없거나 적용되지 않는다는 의미가 실제로 존재할 때만 허용합니다.
- 빈 문자열, `0`, 임의 날짜와 `N/A`를 `NULL` 대신 사용하는 sentinel 값으로 두지 않습니다.
- `NULL`과 빈 문자열을 같은 의미로 사용할지 애플리케이션 경계에서 명시적으로 정규화합니다.
- Default는 business rule을 숨기지 않는 안전한 값에만 사용합니다.
- 생성·수정 시간처럼 DB default를 사용하는 컬럼은 애플리케이션 생성 값과 혼용하지 않습니다.
- nullable unique column의 다중 `NULL` 허용 의미가 제품 요구사항과 맞는지 확인합니다.

## Key와 Constraint

- 모든 테이블은 명시적인 primary key 또는 승인된 대체 식별 전략을 가집니다.
- business invariant는 가능한 경우 unique, foreign key, not-null 또는 check constraint로 DB에서도 보호합니다.
- Foreign key마다 `ON DELETE`와 `ON UPDATE` 동작을 명시적으로 결정합니다.
- Cascade는 데이터 소유권과 생명주기가 같은 경우에만 사용합니다.
- 보호해야 하는 참조 데이터는 restrict/no-action을 사용하고 삭제 실패 동작을 문서화합니다.
- Soft delete를 사용하는 테이블의 unique 의미와 partial unique index 필요성을 검토합니다.
- 애플리케이션 validation만으로 데이터 무결성을 보장하지 않습니다.

## Index

- Index는 실제 query의 filter, join, sort와 cardinality를 근거로 추가합니다.
- Foreign key라고 해서 무조건 index를 추가하지 않고 참조 방향의 조회와 삭제 비용을 검토합니다.
- 복합 index는 선두 컬럼, 정렬 방향과 조회 조건 순서를 근거로 설계합니다.
- Unique constraint가 생성하는 index와 동일한 일반 index를 중복 생성하지 않습니다.
- 낮은 cardinality의 단일 boolean/status index는 실제 선택도와 partial index 가능성을 검토합니다.
- 부분 index, 함수 index, 전문 검색 또는 DB 전용 index는 적용 조건과 portability 비용을 기록합니다.
- 모든 index는 `database-schema-definition.md`에 대상 query 또는 운영 목적을 기록합니다.
- 사용되지 않거나 쓰기 비용이 큰 index는 측정 근거와 migration을 통해 제거합니다.

## 데이터 생명주기

- 생성, 수정, 삭제, 조회 정책은 `resource-lifecycle-policy.md`에서 정의한 제품 규칙을 구현합니다.
- Hard delete, soft delete, archive와 삭제 불가 중 하나를 리소스별로 결정합니다.
- Soft delete 컬럼과 활성 여부 컬럼을 같은 의미로 혼용하지 않습니다.
- 보존 기간, 복구 가능 기간, 연관 데이터 처리와 개인정보 삭제 요구를 기록합니다.
- `created_at`, `updated_at`, 생성자와 수정자 등 audit column 적용 기준을 프로젝트 전체에서 통일합니다.
- Audit 정보가 법적 증적이면 일반 업무 테이블의 수정 가능 column에만 의존하지 않습니다.

## 보안과 개인정보

- 애플리케이션, migration, 조회 전용과 운영 계정의 권한을 최소 권한으로 분리합니다.
- 접속 credential을 코드, migration 또는 문서에 평문으로 저장하지 않습니다.
- 운영 연결은 지원되는 경우 전송 구간 암호화를 사용합니다.
- 비밀번호, 인증 코드와 token 원문을 저장하지 않고 적절한 단방향 hash 또는 암호화 정책을 적용합니다.
- 개인정보와 민감정보 column을 식별하고 접근, 암호화, masking, log와 보존 정책을 연결합니다.
- 운영 데이터 복제본을 개발 또는 테스트 환경에 사용할 때 비식별화와 접근 통제를 적용합니다.

## 검증

- 실제 운영 DB와 호환되는 환경에서 migration과 주요 constraint를 검증합니다.
- `database-review-checklist.md`를 schema 변경 검토에 사용합니다.
- 중요한 query는 실제 또는 대표 데이터 분포에서 실행 계획을 확인합니다.
- schema 정의의 column, constraint와 index가 migration에 실제 존재하는지 자동 또는 수동으로 대조합니다.

## 금지 또는 제한

- 운영 DB에서 검토되지 않은 수동 DDL을 실행하지 않습니다.
- 적용된 migration 파일을 수정해 이력을 다시 쓰지 않습니다.
- persistence entity를 API 계약으로 직접 노출하지 않습니다.
- index 이름이 참조하는 column이 없거나 table 정의와 index 목록이 다른 상태를 허용하지 않습니다.
- 타입과 맞지 않는 default 표현이나 환경마다 다르게 해석되는 값을 사용하지 않습니다.
