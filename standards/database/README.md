# Database Standards

## 목적

`standards/database/`는 Database 종류와 독립적으로 적용되는 물리 schema, 무결성, index와 migration 규칙을 정의합니다.

## 문서

| 문서                                            | 내용                                     |
| ----------------------------------------------- | ---------------------------------------- |
| `DB-01-schema-convention.md`                    | schema source of truth, 명명과 table     |
| `DB-02-column-convention.md`                    | column, type, NULL과 default             |
| `DB-03-constraint-and-index-convention.md`      | key, constraint와 index                  |
| `DB-04-security-and-validation-convention.md`   | 권한, 개인정보와 검증                    |
| `DB-05-migration-convention.md`                 | versioned migration과 변경 절차          |
| `DB-06-migration-compatibility-and-recovery.md` | 호환성, lock과 복구                      |
| `DB-07-reference-data-and-operation.md`         | 기준 데이터와 배포 후 확인               |
| `postgresql/`                                   | PostgreSQL을 선택한 프로젝트의 구현 규칙 |

Database 작업은 이 디렉터리의 공통 규칙을 먼저 적용하고, Requirement에서 PostgreSQL을 선택한 경우 `postgresql/` 규칙을 함께 적용합니다.

Spring Boot에서 관계형 Database를 사용하는 프로젝트는 공통 Database 규칙과 함께 [Spring Boot Flyway Convention](../backend/spring-boot/BE-SPR-06-flyway-convention.md)을 적용합니다.
