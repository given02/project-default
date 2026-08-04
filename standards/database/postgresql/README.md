# PostgreSQL Standards

## 목적

`standards/database/postgresql/`는 Requirement에서 PostgreSQL을 Database로 선택한 프로젝트에 적용할 type, constraint, index, migration과 테스트 규칙을 정의합니다.

## 문서

| 문서                                    | 내용                                     |
| --------------------------------------- | ---------------------------------------- |
| `DB-PG-01-schema-convention.md`         | PostgreSQL 식별자와 type                 |
| `DB-PG-02-schema-feature-convention.md` | constraint, extension과 schema 기능      |
| `DB-PG-03-index-convention.md`          | B-tree, partial, expression과 특수 index |
| `DB-PG-04-migration-convention.md`      | Transactional DDL과 online 변경          |
| `DB-PG-05-testing-convention.md`        | 실제 PostgreSQL schema 및 query 검증     |
