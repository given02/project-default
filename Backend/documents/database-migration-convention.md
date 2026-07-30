# Database Migration Convention

- Owner: Backend Developer
- Purpose: 데이터베이스 schema와 기준 데이터 변경의 작성, 검토, 배포, rollback과 복구 규칙을 정의합니다.
- Audience: Backend Developer와 배포 담당자
- Dependencies: `database-convention.md`, `database-schema-definition.md`, `project-environment.md`
- Next Reading: `database-review-checklist.md`

## 도구와 Source Of Truth

- Migration tool: {{MIGRATION_TOOL_AND_VERSION}}
- Migration 위치: `{{MIGRATION_DIRECTORY}}`
- 실행 명령: `{{MIGRATION_COMMAND}}`
- 상태 확인 명령: `{{MIGRATION_STATUS_COMMAND}}`
- 실행 가능한 schema의 source of truth는 적용된 versioned migration입니다.
- schema dump 또는 생성 DDL을 함께 관리한다면 생성 방법과 검증 책임을 기록합니다.

## 파일 규칙

- 이름 형식: `{{VERSION_OR_TIMESTAMP}}_{{SHORT_DESCRIPTION}}`
- 한 migration은 하나의 설명 가능한 schema 변경 목적을 가집니다.
- 적용된 migration을 수정, 삭제하거나 순서를 바꾸지 않습니다.
- DB object 이름은 `database-convention.md`를 따릅니다.
- 자동 생성 migration도 내용을 검토한 뒤 저장소에 반영합니다.
- 환경별 조건문으로 서로 다른 schema를 만들지 않습니다.

## 변경 절차

1. 관련 요구사항, business rule, domain model과 API 영향을 확인합니다.
2. `database-schema-definition.md`에 변경할 table, column, constraint와 index를 먼저 반영합니다.
3. 호환성, lock, 실행 시간, 저장 공간과 rollback 위험을 분석합니다.
4. migration을 작성합니다.
5. 빈 DB와 현재 운영 버전에 가까운 DB 모두에서 적용을 검증합니다.
6. 애플리케이션의 구버전과 신버전이 전환 기간에 공존할 수 있는지 확인합니다.
7. `database-review-checklist.md`를 통과시킵니다.
8. 배포 후 migration 상태, 오류율, lock, query 성능과 데이터 정합성을 확인합니다.

## 호환 가능한 변경

- 가능한 경우 expand → migrate/backfill → switch → contract 순서를 사용합니다.
- 새 column은 구버전 애플리케이션과 호환되는 nullable 또는 안전한 default로 먼저 추가합니다.
- 대량 backfill은 schema 변경과 분리하고 batch, 중단, 재시작과 진행 확인 방법을 둡니다.
- column/table 이름 변경은 즉시 rename보다 새 구조 추가, 이중 읽기/쓰기 또는 데이터 이전 전략을 검토합니다.
- column 삭제와 constraint 강화는 기존 데이터 및 구버전 코드가 준비된 뒤 수행합니다.
- API 호환성 변경과 schema 변경의 배포 순서를 함께 기록합니다.

## Lock과 대용량 변경

- 대형 테이블 변경은 예상 row 수, lock 수준, 실행 시간과 추가 저장 공간을 검토합니다.
- 지원되는 경우 online/concurrent index 생성 전략을 사용하고 transaction 제한을 확인합니다.
- 긴 transaction과 전체 table rewrite 가능성을 배포 전에 확인합니다.
- 운영 시간대, timeout, 중단 기준과 재시도 절차를 정합니다.
- 위험한 변경은 사전 rehearsal 또는 운영 규모에 가까운 데이터로 검증합니다.

## Rollback과 복구

- Rollback은 down migration 실행만을 의미하지 않습니다.
- 파괴적 변경은 backup, point-in-time recovery, forward fix와 애플리케이션 rollback을 포함해 복구 방법을 기록합니다.
- 이미 데이터가 새 형식으로 쓰인 경우 구버전 애플리케이션 rollback 가능성을 검토합니다.
- 데이터 삭제나 비가역 변환 전에는 복구 가능 여부와 보존 기간을 승인받습니다.
- 실패한 migration의 재실행 안전성과 수동 복구 절차를 명시합니다.

## 기준 및 Seed 데이터

- 애플리케이션 동작에 필수인 기준 데이터와 개발 편의를 위한 sample 데이터를 구분합니다.
- 기준 데이터 변경은 idempotent하고 versioned된 방식으로 관리합니다.
- 운영 환경에 sample, test account 또는 민감한 fixture를 삽입하지 않습니다.
- 환경마다 값이 달라야 하는 설정과 secret을 migration에 hard-code하지 않습니다.

## 검증

- 빈 DB 전체 migration 적용
- 지원하는 기존 버전에서 최신 버전으로 순차 적용
- schema 정의와 실제 schema 비교
- constraint, default, FK 동작과 index 존재 여부 확인
- 대표 query 실행 계획과 성능 확인
- rollback 또는 forward recovery rehearsal
- migration 중 구버전·신버전 애플리케이션 호환성 확인

## 변경 기록 양식

| 항목 | 내용 |
| --- | --- |
| Migration | `{{MIGRATION_ID}}` |
| 목적 | {{PURPOSE}} |
| 영향 table | `{{AFFECTED_TABLES}}` |
| 데이터 변환 | {{DATA_MIGRATION_OR_NONE}} |
| 예상 lock/실행 시간 | {{LOCK_AND_DURATION}} |
| 배포 순서 | {{DEPLOYMENT_SEQUENCE}} |
| 검증 | {{VALIDATION}} |
| Rollback/복구 | {{ROLLBACK_OR_FORWARD_RECOVERY}} |
| 관측 항목 | {{POST_DEPLOY_MONITORING}} |
