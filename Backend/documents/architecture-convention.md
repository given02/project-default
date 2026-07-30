# Backend Architecture Convention

- Owner: Backend Developer
- Purpose: Backend 내부 package, layer와 orchestration 규칙을 정의합니다.
- Audience: Backend Developer
- Dependencies: `../../documents/architecture/architecture.md`, `../../documents/architecture/dependency-rule.md`
- Next Reading: `code-convention.md`

## 구조

- Base namespace 또는 package: `{{BASE_NAMESPACE}}`
- 기능 구성 방식: {{PACKAGE_BY_FEATURE_OR_LAYER}}
- 공통 코드는 `{{COMMON_LOCATION}}`에 두되 도메인 규칙을 포함하지 않습니다.

## 계층 책임

### Interface / Controller

- 외부 요청과 응답 mapping을 담당합니다.
- application use case를 호출합니다.
- persistence 구현을 직접 호출하지 않습니다.
- 비즈니스 규칙을 포함하지 않습니다.

### Application / Service

- use case와 transaction boundary를 담당합니다.
- domain model을 조합하고 port를 호출합니다.
- 여러 domain 또는 외부 시스템에 걸친 orchestration은 명시적으로 문서화합니다.

### Domain

- business invariant와 의미 있는 상태 변경을 담당합니다.
- framework와 전달 형식에 불필요하게 의존하지 않습니다.

### Infrastructure / Repository

- persistence와 외부 시스템 adapter를 담당합니다.
- 외부 모델을 domain 또는 API 모델로 직접 누출하지 않습니다.

## 의존성

허용 방향과 예외는 `../../documents/architecture/dependency-rule.md`를 따릅니다.
