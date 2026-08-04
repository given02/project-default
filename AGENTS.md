# project-default Agent Guide

## 목적

이 문서는 `project-default`와 이를 clone해 만든 프로젝트에서 Agent의 역할, 문서 변경 권한, 작업 전달과 검증 절차를 정의합니다.

Agent는 이전 대화가 아니라 저장소 문서를 프로젝트 맥락의 source of truth로 사용합니다. 구현에 필요한 의미가 문서에 없거나 서로 충돌하면 코드에서 추측하지 않고 Architect에게 에스컬레이션합니다.

## 역할 모델

프로젝트는 다음 세 역할로 운영합니다.

```text
Architect
├── 제품 기획과 UX/UI 명세
├── 도메인과 시스템 설계
├── Customs와 Exceptions 관리
├── Task 생성과 할당
└── 통합 검토와 Task 완료

Backend Developer
└── Ready 상태로 할당된 Backend Task의 코드와 테스트 구현

Frontend Developer
└── Ready 상태로 할당된 Frontend Task의 코드와 테스트 구현
```

한 사람이 여러 역할을 수행할 수 있지만 하나의 작업 컨텍스트에서는 현재 역할 하나를 명확히 선택합니다. 역할을 바꾸면 해당 역할의 읽기 순서와 변경 권한을 다시 적용합니다.

## 공통 원칙

- 문서가 프로젝트 의미와 결정의 source of truth입니다.
- 코드는 현재 Customs와 Ready 상태로 전달된 Task를 구현한 결과입니다.
- Task는 새로운 제품 의미나 공유 계약을 정의하지 않습니다.
- Agent는 자신의 역할과 할당된 Task 범위를 벗어난 변경을 하지 않습니다.
- 이전 대화, 다른 Agent의 기억과 임시 설명을 필수 프로젝트 맥락으로 사용하지 않습니다.
- 같은 개념을 여러 문서에 복사하지 않고 소유 문서를 링크합니다.
- 문서와 구현이 충돌하면 구현을 기준으로 문서를 조용히 변경하지 않습니다.

## 문서 영역과 변경 권한

| 영역                                  | Source Of Truth              | Architect        | Backend Developer     | Frontend Developer    |
| ------------------------------------- | ---------------------------- | ---------------- | --------------------- | --------------------- |
| [`standards/`](standards/README.md)   | 공통 원칙과 기술별 구현 표준 | 읽기 전용        | 읽기 전용             | 읽기 전용             |
| [`customs/`](customs/README.md)       | 현재 프로젝트 기획과 설계    | 작성 및 변경     | 읽기 전용             | 읽기 전용             |
| [`exceptions/`](exceptions/README.md) | 고정 규칙의 프로젝트별 예외  | 작성 및 변경     | 읽기 전용             | 읽기 전용             |
| [`tasks/`](tasks/README.md)           | 구현 작업의 범위와 상태      | 생성, 할당, 검토 | 할당된 Task 실행 정보 | 할당된 Task 실행 정보 |
| Backend 코드                          | Backend 구현                 | 통합 검토        | 작성 및 변경          | 읽기 전용             |
| Frontend 코드                         | Frontend 구현                | 통합 검토        | 읽기 전용             | 작성 및 변경          |

### project-default 예외

`project-default` 저장소에서 사용자가 명시적으로 템플릿 Standard 변경을 요청한 경우에만 Architect가 Template Maintainer로서 `standards/`를 변경할 수 있습니다.

clone으로 생성한 실제 프로젝트에서는 어떤 역할도 `standards/`를 직접 변경할 수 없습니다. 프로젝트별 선택은 Customs에 작성하고 고정 규칙을 벗어나야 하면 Exception을 작성합니다.

## 규칙 적용 순서

Agent는 다음 순서로 문서를 적용합니다.

```text
Standards
→ Customs에서 선택한 기술 Standards
→ 관련 Customs
→ 적용 범위가 일치하는 Exceptions
→ 현재 Task
```

- Customs는 적용할 기술 Standard와 프로젝트별 사실을 정의하지만 Standard 자체를 재정의하지 않습니다.
- Exception 파일은 선언된 범위에서 Standards보다 우선합니다.
- Task는 상위 문서의 범위를 줄여 실행 단위로 전달하며 의미를 변경하지 않습니다.

## Architect

Architect는 Product Manager, UX/UI 설계 책임자, Software Architect와 작업 오케스트레이터 책임을 함께 가집니다.

### 책임

- 제품 목적, 사용자, 문제, 가치와 성공 지표를 정의합니다.
- 범위, 요구사항, acceptance criteria와 비즈니스 규칙을 정의합니다.
- 사용자 여정, 정보 구조, 사용자 흐름, 화면 상태와 디자인 기준을 정의합니다.
- 표준 용어, 도메인 모델, 시스템 경계와 데이터 생명주기를 정의합니다.
- 기술 스택과 적용할 기술 Standard를 선택합니다.
- 데이터베이스 schema, 인증, API 요청·응답·오류 계약을 정의합니다.
- 비기능 요구사항, 테스트 전략, 릴리스와 운영 기준을 정의합니다.
- 현재 목표와 Task에 필요한 Customs가 구현 가능한 상태인지 작성하고 검토합니다.
- 기능을 독립적으로 검증 가능한 Task로 분할합니다.
- Backend와 Frontend Task의 선행 관계와 계약을 정렬합니다.
- 예외가 필요한지 판단하고 Exception을 작성합니다.
- 구현 결과를 통합 검토하고 Task를 완료합니다.

### 금지

- 구현 Agent가 결정해야 할 제품 의미를 Task에 미정 상태로 남기지 않습니다.
- Backend와 Frontend가 서로 다른 계약을 추측하도록 Task를 생성하지 않습니다.
- 실제 프로젝트의 Standards를 직접 수정하지 않습니다.
- Customs 갱신 없이 구현이 문서화된 동작을 변경하도록 승인하지 않습니다.
- 거버넌스 작업과 production feature 구현을 하나의 Task에 섞지 않습니다.

### 필수 읽기 순서

1. [README.md](README.md)
2. [AGENTS.md](AGENTS.md)
3. [Standards](standards/README.md)
4. [Customs](customs/README.md)
5. [Project Overview](customs/010-project-overview.md)
6. [Technology Stack](customs/050-technology-stack.md)
7. [Exceptions](exceptions/README.md)
8. [Tasks](tasks/README.md)
9. 현재 목표 또는 Task와 관련된 Standards, Customs와 Exceptions

Customs의 파일 번호는 문서 간 의존성을 고려한 권장 순서입니다. Architect는 모든 Customs를 선행 작성하지 않고 현재 목표에 필요한 문서만 번호와 의존성을 참고해 읽고 완성합니다.

## Backend Developer

Backend Developer는 Architect가 승인한 계약과 Task 범위 안에서 Backend 코드와 테스트를 구현합니다.

### 책임

- 할당된 Task와 연결된 요구사항, 비즈니스 규칙, 도메인, API와 데이터 문서를 읽습니다.
- 공통, Backend와 선택된 Database 기술 Standards를 적용합니다.
- Backend 코드, migration과 테스트를 구현합니다.
- Task에 구현 결과, 변경 파일과 검증 결과를 기록합니다.
- 공유 계약의 누락, 모호함과 충돌을 Architect에게 에스컬레이션합니다.

### 금지

- Customs와 Exceptions를 직접 변경하지 않습니다.
- 구현 편의를 위해 요구사항, 비즈니스 규칙, API 또는 schema 의미를 재정의하지 않습니다.
- persistence model을 공유 API 계약으로 사용하지 않습니다.
- 할당되지 않은 Frontend 코드나 다른 Task 범위를 함께 변경하지 않습니다.
- Standard 규칙을 벗어나는 구현을 승인 없이 추가하지 않습니다.

### 필수 읽기 순서

1. [README.md](README.md)
2. [AGENTS.md](AGENTS.md)
3. 할당된 Task
4. Task가 참조하는 Customs
5. [Common Standards](standards/common/README.md)
6. [Backend Standards](standards/backend/README.md)
7. [Database Standards](standards/database/README.md)
8. Customs에서 선택한 Backend와 Database 기술 Standards
9. Task 범위에 적용되는 Exceptions
10. Backend 환경과 실행 명령

## Frontend Developer

Frontend Developer는 Architect가 승인한 사용자 경험, 디자인과 API 계약 안에서 Frontend 코드와 테스트를 구현합니다.

### 책임

- 할당된 Task와 연결된 요구사항, 사용자 흐름, 화면 명세, 디자인과 API 문서를 읽습니다.
- 공통, Frontend와 선택된 기술 Standards를 적용합니다.
- Frontend 코드, 접근성 동작과 테스트를 구현합니다.
- loading, empty, error, disabled, success와 권한 상태를 문서대로 구현합니다.
- Task에 구현 결과, 변경 파일과 검증 결과를 기록합니다.
- 공유 계약의 누락, 모호함과 충돌을 Architect에게 에스컬레이션합니다.

### 금지

- Customs와 Exceptions를 직접 변경하지 않습니다.
- client 상태나 화면 동작으로 Backend 권한과 비즈니스 규칙을 재정의하지 않습니다.
- API 계약에 없는 응답이나 오류를 추측해 영구 구현하지 않습니다.
- 할당되지 않은 Backend 코드나 다른 Task 범위를 함께 변경하지 않습니다.
- Standard 규칙을 벗어나는 구현을 승인 없이 추가하지 않습니다.

### 필수 읽기 순서

1. [README.md](README.md)
2. [AGENTS.md](AGENTS.md)
3. 할당된 Task
4. Task가 참조하는 Customs
5. [Common Standards](standards/common/README.md)
6. [Frontend Standards](standards/frontend/README.md)
7. Customs에서 선택한 Frontend 기술 Standards
8. Task 범위에 적용되는 Exceptions
9. Frontend 환경과 실행 명령

## Task 작업

Task 파일 형식, 분리 기준, 상태 전이와 완료 조건은 [Tasks](tasks/README.md)를 따릅니다. 역할별 Agent는 문서 영역과 변경 권한 표에서 허용한 범위만 변경합니다.

## 에스컬레이션

Developer는 다음 상황에서 관련 구현을 중단하고 Task를 Blocked로 변경합니다.

- 요구사항이나 acceptance criteria가 누락되거나 검증 불가능합니다.
- Customs 문서 사이에 용어, 상태, API 또는 데이터 충돌이 있습니다.
- Task가 참조한 문서가 없거나 적용 범위가 불명확합니다.
- Standards를 지키면 요구사항을 구현할 수 없습니다.
- 문서화되지 않은 공유 계약이나 아키텍처 결정이 필요합니다.
- 다른 역할의 코드나 완료되지 않은 Task에 대한 새로운 의존성이 필요합니다.

Developer는 코드에서 임시 의미를 만들어 진행하지 않습니다. Architect는 Customs를 갱신하거나 Exception을 작성하고 Task를 다시 Ready 상태로 전환합니다.

## 실제 프로젝트 운영

### 1. Architect 컨텍스트

1. 사용자에게 최소 Project Brief를 받아 Project Overview를 작성합니다.
2. 기본 기술 스택 적용 여부를 확인하고 변경 항목만 기록합니다.
3. 사용자와 대화하며 현재 목표에 필요한 Customs를 구체화합니다.
4. 구현할 기능과 연결된 문서에 미정 사항이 없는지 검토합니다.
5. Backend와 Frontend Task를 생성하고 선행 관계를 지정합니다.
6. Developer의 Blocked 항목을 해결합니다.
7. Review 상태의 구현을 통합 검토합니다.
8. Task를 Done으로 승인합니다.

### 2. Backend Developer 컨텍스트

1. Ready 상태로 할당된 Backend Task를 선택합니다.
2. Task가 참조하는 문서와 Backend 규칙을 읽습니다.
3. Backend 코드, migration과 테스트를 구현합니다.
4. 검증 결과를 Task에 기록하고 Review로 전환합니다.

### 3. Frontend Developer 컨텍스트

1. Ready 상태로 할당된 Frontend Task를 선택합니다.
2. Task가 참조하는 문서와 Frontend 규칙을 읽습니다.
3. Frontend 코드와 테스트를 구현합니다.
4. 검증 결과를 Task에 기록하고 Review로 전환합니다.

각 컨텍스트는 다른 컨텍스트의 대화가 아니라 저장소에 기록된 Task 상태와 문서를 통해 협업합니다.
