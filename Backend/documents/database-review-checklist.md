# Database Review Checklist

- Owner: Backend Developer
- Purpose: 데이터베이스 기준선과 schema 변경의 완전성, 정합성, 안전성을 검토합니다.
- Audience: Backend Developer, Architect와 변경 검토자
- Dependencies: `database-convention.md`, `database-schema-definition.md`, `database-migration-convention.md`
- Next Reading: `resource-lifecycle-policy.md`

## 요구사항과 소유권

- [ ] 변경이 승인된 요구사항과 business rule에 연결되어 있습니다.
- [ ] table과 데이터의 소유 Aggregate 또는 컴포넌트가 명확합니다.
- [ ] 공유 도메인 의미를 persistence 문서에서 새로 정의하지 않습니다.
- [ ] 중복 저장 데이터에는 갱신 책임과 정합성 복구 방법이 있습니다.

## Table과 Column

- [ ] 모든 table과 column에 의미 있는 이름과 설명이 있습니다.
- [ ] PK, FK, nullable, default와 데이터 타입이 명시되어 있습니다.
- [ ] Identifier, 날짜·시간, boolean, enum과 금액 타입이 프로젝트 규칙과 일치합니다.
- [ ] 타입과 default 표현이 실제 DB에서 유효합니다.
- [ ] `NULL`, 빈 문자열, `0`, `N/A`의 의미를 혼용하지 않습니다.
- [ ] 상태 값의 허용 범위와 전이가 정의되어 있습니다.
- [ ] audit column과 생성·수정 책임이 일관됩니다.

## 관계와 Constraint

- [ ] 모든 FK가 존재하는 table과 column을 참조합니다.
- [ ] FK의 타입이 참조 대상 key와 호환됩니다.
- [ ] 모든 FK에 ON DELETE와 ON UPDATE 동작이 결정되어 있습니다.
- [ ] Unique와 check constraint가 관련 business invariant를 보호합니다.
- [ ] nullable unique와 soft delete가 중복 허용 의미를 깨뜨리지 않습니다.
- [ ] Cascade가 데이터 소유권과 생명주기에 맞습니다.

## Index와 Query

- [ ] 모든 index가 존재하는 table과 column만 참조합니다.
- [ ] table별 index 정의와 전체 index 목록이 일치합니다.
- [ ] 각 index에 filter, join, sort 또는 운영 목적이 기록되어 있습니다.
- [ ] 복합 index의 column 순서와 정렬 방향에 근거가 있습니다.
- [ ] unique constraint와 동일한 중복 index가 없습니다.
- [ ] 낮은 cardinality index와 과도한 index의 쓰기 비용을 검토했습니다.
- [ ] 중요한 query의 실행 계획을 대표 데이터 분포에서 확인했습니다.

## 생명주기와 보안

- [ ] 생성, 수정, 삭제, 조회 정책이 관련 business rule을 구현합니다.
- [ ] hard delete, soft delete, archive와 삭제 불가 정책이 명확합니다.
- [ ] 보존, 복구, 연관 데이터와 개인정보 삭제 정책이 정의되어 있습니다.
- [ ] 개인정보와 민감정보 column이 식별되어 있습니다.
- [ ] hash, 암호화, masking과 접근 권한 정책이 적용되어 있습니다.
- [ ] secret 또는 운영 개인정보가 migration, log와 fixture에 포함되지 않습니다.

## Migration과 운영

- [ ] `database-schema-definition.md`가 migration보다 먼저 또는 같은 작업에서 갱신되었습니다.
- [ ] migration이 빈 DB와 지원하는 기존 버전에서 성공합니다.
- [ ] 적용된 migration 파일을 수정하지 않았습니다.
- [ ] 구버전·신버전 애플리케이션의 배포 중 호환성을 확인했습니다.
- [ ] 대형 table의 lock, 실행 시간, 저장 공간과 운영 시간대를 검토했습니다.
- [ ] backfill은 batch, 재시작과 진행 확인 방법을 가집니다.
- [ ] 실패 시 rollback 또는 forward recovery 절차가 있습니다.
- [ ] 배포 후 migration 상태, lock, 오류율, query 성능과 정합성 관측 방법이 있습니다.

## 최종 정합성

- [ ] 용어집, domain model, API 계약, schema 정의와 코드가 같은 용어를 사용합니다.
- [ ] schema 정의의 table, column, constraint와 index가 실제 migration에 존재합니다.
- [ ] 존재하지 않는 column을 참조하는 index, constraint 또는 문서 항목이 없습니다.
- [ ] 관련 integration test와 migration 검증이 통과했습니다.
