# Persistence Convention

- Owner: Backend Developer
- Purpose: 애플리케이션과 persistence 계층 사이의 모델 mapping, 조회와 transaction 구현 규칙을 정의합니다.
- Audience: Backend Developer
- Dependencies: `../../documents/architecture/domain-model.md`, `database-convention.md`, `resource-lifecycle-policy.md`
- Next Reading: `database-convention.md`

## 경계

- 이 문서는 애플리케이션 코드에서 persistence를 사용하는 방법의 source of truth입니다.
- 물리 schema, 데이터 타입, constraint와 index 규칙은 `database-convention.md`에서 관리합니다.
- 실제 테이블 정의는 `database-schema-definition.md`에서 관리합니다.
- schema 변경 절차는 `database-migration-convention.md`에서 관리합니다.
- 제품 의미와 데이터 생명주기는 공유 비즈니스 규칙과 `resource-lifecycle-policy.md`를 따릅니다.

## 적용 여부와 기술

- Persistence 사용 여부: {{PERSISTENCE_REQUIRED}}
- 기술: {{DATABASE_AND_ACCESS_LIBRARY}}
- Mapping 방식: {{ORM_DATA_MAPPER_OR_SQL}}

## 모델 Mapping

- persistence model을 API 응답으로 직접 반환하지 않습니다.
- domain model, persistence model과 API model을 같은 타입으로 사용할지 명시적으로 결정합니다.
- persistence 편의를 위해 domain invariant를 약화하지 않습니다.
- 외부 라이브러리와 DB 전용 타입은 persistence 경계 밖으로 불필요하게 노출하지 않습니다.
- nullable, enum, identifier와 시간 값의 mapping을 `database-convention.md`와 일치시킵니다.

## 조회

- repository 또는 query port는 호출자가 필요한 의도를 드러내는 인터페이스를 제공합니다.
- N+1, 무제한 조회와 불필요한 eager loading을 피합니다.
- 대량 목록은 문서화된 pagination 또는 streaming 정책을 사용합니다.
- projection을 사용할 때 domain model을 우회하여 business invariant를 변경하지 않습니다.
- 중요한 query는 예상 실행 계획과 `database-schema-definition.md`의 index 근거를 함께 검토합니다.

## Transaction과 동시성

- transaction boundary는 application/service 계층에 둡니다.
- transaction 안에서 불필요한 외부 네트워크 호출을 수행하지 않습니다.
- isolation level, lock, optimistic concurrency와 retry가 필요하면 사용 조건을 문서화합니다.
- retry 가능한 transaction은 idempotency와 중복 실행 결과를 함께 설계합니다.
- 여러 데이터 저장소에 걸친 일관성이 필요하면 outbox, saga 또는 보상 정책을 ADR로 결정합니다.

## 테스트

- 운영 DB와 의미가 다른 in-memory DB 사용 여부를 명시적으로 결정합니다.
- 중요한 query와 constraint는 실제 DB 호환 통합 테스트로 검증합니다.
- transaction rollback, lock 경합, unique 충돌과 동시 갱신 경로를 위험도에 비례해 검증합니다.
