# Database Schema Definition

- Owner: Backend Developer
- Purpose: 프로젝트별 테이블, column, 관계, constraint와 index를 구현 전에 정의하는 양식을 제공합니다.
- Audience: Backend Developer, Architect와 데이터베이스 변경 검토자
- Dependencies: `database-convention.md`, `../../documents/architecture/domain-model.md`, `../../documents/product/business-rule.md`
- Next Reading: `database-migration-convention.md`

## 사용 규칙

- 프로젝트 초기화 시 이 문서의 플레이스홀더를 실제 값으로 교체합니다.
- 테이블마다 아래의 동일한 정의 형식을 사용합니다.
- 제품 의미와 invariant는 이 문서에 새로 만들지 않고 관련 요구사항, business rule과 domain model을 링크합니다.
- 실행 가능한 schema의 source of truth는 versioned migration이며 이 문서는 검토 가능한 설계 계약입니다.
- table 정의와 전체 constraint/index 목록을 같은 작업에서 일치시킵니다.
- ERD를 사용하더라도 column, nullable, default와 constraint의 상세 정의를 이 문서에서 생략하지 않습니다.

## 개요

| 항목 | 결정 |
| --- | --- |
| Database 및 버전 | {{DATABASE_AND_VERSION}} |
| 기본 schema | {{DEFAULT_SCHEMA}} |
| Identifier 전략 | {{IDENTIFIER_STRATEGY}} |
| 날짜·시간 정책 | {{DATE_TIME_POLICY}} |
| Enum 정책 | {{ENUM_POLICY}} |
| Migration 도구 | {{MIGRATION_TOOL}} |
| 기준 migration | {{BASELINE_MIGRATION_OR_VERSION}} |

## 테이블 목록

| No | 테이블 | 설명 | 소유 Aggregate/컴포넌트 | 예상 규모 | 관련 문서 |
| --- | --- | --- | --- | --- | --- |
| 1 | `{{TABLE_NAME}}` | {{DESCRIPTION}} | {{DATA_OWNER}} | {{EXPECTED_VOLUME}} | `BR-{{NUMBER}}`, `REQ-{{NUMBER}}` |

## 관계 목록

| 출발 테이블 | 관계 | 도착 테이블 | FK | Nullable | ON DELETE | 소유권과 이유 |
| --- | --- | --- | --- | --- | --- | --- |
| `{{CHILD_TABLE}}` | N:1 | `{{PARENT_TABLE}}` | `{{FK_COLUMN}}` | {{YES_OR_NO}} | {{RESTRICT_CASCADE_SET_NULL}} | {{OWNERSHIP_REASON}} |

## 테이블 정의 양식

아래 절을 테이블별로 복사해 작성합니다.

### `{{TABLE_NAME}}`

| 항목 | 내용 |
| --- | --- |
| 설명 | {{TABLE_DESCRIPTION}} |
| 소유 Aggregate/컴포넌트 | {{DATA_OWNER}} |
| 관련 요구사항 | `REQ-{{NUMBER}}` |
| 관련 비즈니스 규칙 | `BR-{{NUMBER}}` |
| 주요 조회 패턴 | {{PRIMARY_ACCESS_PATTERNS}} |
| 예상 row 수와 증가율 | {{EXPECTED_ROWS_AND_GROWTH}} |
| 보존 기간 | {{RETENTION_POLICY}} |
| 민감정보 포함 여부 | {{SENSITIVE_DATA_OR_NONE}} |

#### Persistence 생명주기

| 동작 | 구현 정책 | 관련 규칙 |
| --- | --- | --- |
| Create | {{CREATE_POLICY}} | `BR-{{NUMBER}}` |
| Read | {{READ_POLICY}} | `BR-{{NUMBER}}` |
| Update | {{UPDATE_POLICY}} | `BR-{{NUMBER}}` |
| Delete | {{HARD_DELETE_SOFT_DELETE_ARCHIVE_RESTRICT}} | `BR-{{NUMBER}}` |

#### Column

| Column | 데이터 타입 | PK | FK | Nullable | Default | 설명 | 민감도/비고 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `{{COLUMN_NAME}}` | `{{DATA_TYPE}}` | {{Y_OR_BLANK}} | `{{REFERENCED_TABLE_COLUMN_OR_BLANK}}` | {{Y_OR_N}} | `{{DEFAULT_OR_NONE}}` | {{DESCRIPTION}} | {{CLASSIFICATION_OR_NOTE}} |

#### Constraint

| 종류 | 이름 | Column/조건 | 참조 | 동작 또는 의미 |
| --- | --- | --- | --- | --- |
| PRIMARY KEY | `pk_{{TABLE}}` | `{{COLUMN}}` | 해당 없음 | {{MEANING}} |
| FOREIGN KEY | `fk_{{TABLE}}_{{TARGET}}` | `{{COLUMN}}` | `{{TARGET_TABLE}}({{TARGET_COLUMN}})` | ON DELETE {{ACTION}}, ON UPDATE {{ACTION}} |
| UNIQUE | `uk_{{TABLE}}_{{MEANING}}` | `{{COLUMN_LIST}}` | 해당 없음 | {{DUPLICATE_PREVENTION_RULE}} |
| CHECK | `ck_{{TABLE}}_{{RULE}}` | `{{CHECK_EXPRESSION}}` | 해당 없음 | {{INVARIANT}} |

#### Index

| 이름 | 종류 | Column과 정렬 | 조건 | 대상 query/운영 목적 |
| --- | --- | --- | --- | --- |
| `idx_{{TABLE}}_{{PURPOSE}}` | {{BTREE_GIN_GIST_OR_OTHER}} | `{{COLUMN_1}} ASC, {{COLUMN_2}} DESC` | {{PREDICATE_OR_NONE}} | {{FILTER_JOIN_SORT_OR_OPERATION}} |

#### 상태 또는 코드 값

| Column | 값 | 의미 | 허용 전이 | 폐기 정책 |
| --- | --- | --- | --- | --- |
| `{{STATUS_COLUMN}}` | `{{VALUE}}` | {{MEANING}} | {{ALLOWED_TRANSITIONS}} | {{DEPRECATION_POLICY}} |

## 전체 Constraint 목록

테이블별 정의와 중복되는 설명을 새로 만들지 않고 검색과 충돌 검토를 위한 인덱스로 사용합니다.

| 종류 | 이름 | 테이블 | Column/조건 | 관련 규칙 |
| --- | --- | --- | --- | --- |
| {{PK_FK_UNIQUE_CHECK}} | `{{CONSTRAINT_NAME}}` | `{{TABLE_NAME}}` | `{{COLUMNS_OR_EXPRESSION}}` | `BR-{{NUMBER}}` |

## 전체 Index 목록

| 이름 | 테이블 | Column과 정렬 | 조건 | 대상 query/운영 목적 | 근거 문서 |
| --- | --- | --- | --- | --- | --- |
| `{{INDEX_NAME}}` | `{{TABLE_NAME}}` | `{{COLUMNS_AND_ORDER}}` | {{PREDICATE_OR_NONE}} | {{PURPOSE}} | {{QUERY_OR_REQUIREMENT_LINK}} |

## 설계 검토 기록

| 날짜 | 변경 요약 | 관련 migration | 관련 결정/ADR | 검토 상태 |
| --- | --- | --- | --- | --- |
| YYYY-MM-DD | {{CHANGE_SUMMARY}} | `{{MIGRATION_ID}}` | {{DECISION_OR_ADR}} | 제안됨 |

## 완료 기준

- 모든 table, column, PK, FK, nullable과 default가 정의되어 있습니다.
- 모든 FK의 삭제 및 수정 동작이 정의되어 있습니다.
- business invariant가 constraint 또는 명시적인 애플리케이션 검증에 연결되어 있습니다.
- 모든 index에 실제 query 또는 운영 목적이 있습니다.
- table별 index 표와 전체 index 목록이 일치합니다.
- index와 constraint가 존재하지 않는 table 또는 column을 참조하지 않습니다.
- 상태 값과 허용 범위가 문서화되어 있습니다.
- 개인정보, 보존과 삭제 정책이 연결되어 있습니다.
- migration과 이 문서가 일치합니다.
