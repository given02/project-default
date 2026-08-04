# project-default Agent Guide

## 목적

이 문서는 `project-default`와 이를 clone해 만든 프로젝트에서 Agent의 역할, 문서 변경 권한, 요구사항 전달과 검증 절차를 정의합니다.

Agent는 이전 대화가 아니라 저장소 문서를 프로젝트 맥락의 source of truth로 사용합니다. 구현에 필요한 의미가 문서에 없거나 서로 충돌하면 코드에서 추측하지 않고 Architect에게 에스컬레이션합니다.

## `start` 명령

사용자가 공백을 제외하고 `start`만 입력하면 대소문자와 관계없이 [START.md](standards/START.md)를 읽고 그 절차를 실행합니다.

- 첫 응답에서는 프로젝트 설명과 다섯 산출물에 대응하는 Google Sheets 및 Figma 링크를 요청합니다.
- 답변을 받기 전에 프로젝트 파일, Requirement 또는 production 코드를 만들지 않습니다.
- 사용자가 답변하면 `customs/PROJECT.md`에 프로젝트 설명과 산출물 링크를 기록합니다.
- 요구사항·기능 명세 통합 Google Sheets와 테스트 시나리오 및 결과 Google Sheets는 필수입니다.
- 화면 또는 Database가 없는 프로젝트는 해당 산출물에 `해당 없음`을 허용합니다.
- 링크에 직접 접근할 수 없으면 접근 가능한 것처럼 행동하지 않고 반영할 내용을 사용자에게 제공합니다.

## 역할 모델

```text
Architect
├── 요구사항과 설계 작성
├── Requirement 생성과 Ready 승인
├── Exceptions 관리
└── 구현 통합 검토와 Done 승인

Backend Developer
└── Ready Requirement의 Backend 코드, 테스트와 결과 기록

Frontend Developer
└── Ready Requirement의 Frontend 코드, 테스트와 결과 기록
```

한 사람이 여러 역할을 수행할 수 있지만 하나의 작업 컨텍스트에서는 현재 역할 하나를 명확히 선택합니다. 역할을 바꾸면 해당 역할의 읽기 순서와 변경 권한을 다시 적용합니다.

## 공통 원칙

- 문서가 프로젝트 의미와 결정의 source of truth입니다.
- 하나의 Requirement 파일이 제품 명세와 구현 작업을 함께 소유합니다.
- Google Sheets와 Figma는 검토와 공유를 위한 산출물이며 저장소 Requirement와 같은 작업에서 동기화합니다.
- 코드는 Ready 상태로 전달된 Requirement를 구현한 결과입니다.
- Agent는 현재 Requirement 범위를 벗어난 변경을 하지 않습니다.
- 이전 대화나 다른 Agent의 기억을 필수 프로젝트 맥락으로 사용하지 않습니다.
- 같은 개념을 여러 Requirement에 복사하지 않고 소유 Requirement ID를 참조합니다.
- 문서와 구현이 충돌하면 구현을 기준으로 문서를 조용히 변경하지 않습니다.

## 문서 영역과 변경 권한

| 영역                                  | Source Of Truth                     | Architect               | Backend Developer                         | Frontend Developer                        |
| ------------------------------------- | ----------------------------------- | ----------------------- | ----------------------------------------- | ----------------------------------------- |
| [`standards/`](standards/README.md)   | 공통 원칙과 기술별 구현 표준        | 읽기 전용               | 읽기 전용                                 | 읽기 전용                                 |
| [`standards/START.md`](standards/START.md)         | start 초기 질문과 절차            | 읽기 전용               | 읽기 전용                                 | 읽기 전용                                 |
| [`standards/ARTIFACTS.md`](standards/ARTIFACTS.md) | 외부 산출물 생성 규격과 작성 규칙 | 읽기 전용               | 읽기 전용                                 | 읽기 전용                                 |
| [`customs/`](customs/README.md)       | 요구사항, 설계, 상태와 검증 증거    | 생성, 명세, 검토와 승인 | 상태, Blocked, Backend 구현과 테스트 기록 | 상태, Blocked, Frontend 구현과 테스트 기록 |
| [`exceptions/`](exceptions/README.md) | 고정 규칙의 프로젝트별 예외         | 작성 및 변경            | 읽기 전용                                 | 읽기 전용                                 |
| Backend 코드                          | Backend 구현                        | 통합 검토               | 작성 및 변경                              | 읽기 전용                                 |
| Frontend 코드                         | Frontend 구현                       | 통합 검토               | 읽기 전용                                 | 작성 및 변경                              |

Developer는 Customs에서 상태, Blocked, 자신이 담당한 구현 결과와 테스트 결과만 변경합니다. 요구사항, 기능 명세, 화면 설계, Database 설계와 테스트 계획의 의미를 변경해야 하면 Architect에게 요청합니다.

### project-default 예외

`project-default` 저장소에서 사용자가 명시적으로 템플릿 Standard 변경을 요청한 경우에만 Architect가 Template Maintainer로서 `standards/`를 변경할 수 있습니다.

clone으로 생성한 실제 프로젝트에서는 어떤 역할도 `standards/`를 직접 변경할 수 없습니다. Standard를 벗어나야 하면 Exception을 작성합니다.

## 규칙 적용 순서

```text
Standards
→ 현재 Requirement
→ 적용 범위가 일치하는 Exceptions
```

- Requirement는 프로젝트별 의미, 설계, 구현 범위와 검증 기준을 정의하지만 Standard 자체를 재정의하지 않습니다.
- Exception 파일은 선언된 범위에서 Standards보다 우선합니다.
- 코드와 테스트는 Requirement의 의미와 범위를 변경하지 않습니다.

## Requirement 상태

```text
Draft
→ Ready
→ In Progress
├── Blocked
└── Review
    → Done

Blocked
→ Ready

Draft | Ready | In Progress | Blocked | Review
→ Cancelled
```

- `Draft`: 명세와 테스트 계획을 작성 중이며 구현하지 않습니다.
- `Ready`: 구현에 필요한 결정과 테스트 계획이 완료되어 구현을 시작할 수 있습니다.
- `In Progress`: 코드와 테스트를 작성하고 있습니다.
- `Blocked`: 누락된 결정, 충돌 또는 선행 조건 때문에 진행할 수 없습니다.
- `Review`: 구현과 테스트 결과가 기록되어 통합 검토를 기다립니다.
- `Done`: 명세, 구현, 테스트와 검토가 일치합니다.
- `Cancelled`: 더 이상 구현하지 않으며 취소 이유와 영향을 기록했습니다.

Review에서 변경이 필요하면 In Progress로 되돌립니다. 구현 중 명세 변경이 필요하면 Architect가 관련 구역을 갱신하고 다시 Ready로 승인합니다.

## Architect

Architect는 Product Manager, UX/UI 설계 책임자, Software Architect와 작업 오케스트레이터 책임을 함께 가집니다.

### 책임

- 사용자의 설명에서 독립적으로 검증 가능한 사용자 결과를 식별합니다.
- Requirement 파일을 만들고 요구사항, 기능 명세, 화면 설계와 Database 설계를 순서대로 작성합니다.
- 구현 전에 테스트 항목, 기대 결과와 검증 방법을 정의합니다.
- 요구사항 정의와 기능 명세는 통합 Google Sheets의 지정 시트, 화면 설계는 Figma, Database 설계는 DB 테이블 정의 Google Sheets, 테스트 계획은 테스트 시나리오 및 결과 Google Sheets에 반영합니다.
- 외부 산출물의 링크와 반영 위치를 Requirement에 기록합니다.
- 기술 선택, 비즈니스 규칙, API, 인증, 데이터와 운영 제약을 현재 Requirement에 필요한 수준으로 확정합니다.
- Requirement가 Ready 기준을 충족하는지 검토합니다.
- Backend와 Frontend의 구현 순서와 공유 계약을 정렬합니다.
- Exception이 필요한지 판단하고 작성합니다.
- 구현 및 테스트 결과를 통합 검토하고 Done으로 승인합니다.

### 금지

- 구현 Agent가 결정해야 할 제품 의미를 미정 상태로 남긴 채 Ready로 전환하지 않습니다.
- Backend와 Frontend가 서로 다른 계약을 추측하도록 명세를 작성하지 않습니다.
- 실제 프로젝트의 Standards를 직접 수정하지 않습니다.
- Requirement 갱신 없이 구현이 문서화된 동작을 변경하도록 승인하지 않습니다.
- 독립적으로 검증할 수 없는 여러 사용자 결과를 하나의 Requirement에 묶지 않습니다.

### 필수 읽기 순서

1. [README.md](README.md)
2. [AGENTS.md](AGENTS.md)
3. [Standards](standards/README.md)
4. [Customs](customs/README.md)
5. [Artifact Templates](standards/ARTIFACTS.md)
6. [Exceptions](exceptions/README.md)
7. 현재 Requirement와 참조된 선행 Requirement
8. 현재 Requirement에 적용되는 Standards와 Exceptions

## Backend Developer

Backend Developer는 Ready 상태로 승인된 Requirement 범위 안에서 Backend 코드와 테스트를 구현합니다.

### 책임

- 현재 Requirement의 기능, Business Rule, API와 Database 설계를 읽습니다.
- 공통, Backend와 선택된 Database 기술 Standards를 적용합니다.
- Backend 코드, migration과 테스트를 구현합니다.
- Requirement에 변경 파일, 구현 요약, 검증 명령과 실제 결과를 기록합니다.
- 접근할 수 있다면 실제 테스트 결과를 Google Sheets 테스트 시나리오 및 결과서에도 반영합니다.
- 공유 계약의 누락, 모호함과 충돌을 Architect에게 에스컬레이션합니다.

### 금지

- Requirement의 명세와 Exceptions를 직접 변경하지 않습니다.
- 구현 편의를 위해 요구사항, API 또는 Database 의미를 재정의하지 않습니다.
- persistence model을 공유 API 계약으로 사용하지 않습니다.
- 현재 Requirement에 포함되지 않은 Frontend 코드나 다른 요구사항을 함께 변경하지 않습니다.
- Standard 규칙을 벗어나는 구현을 승인 없이 추가하지 않습니다.

### 필수 읽기 순서

1. [README.md](README.md)
2. [AGENTS.md](AGENTS.md)
3. 현재 Requirement
4. 참조된 선행 Requirement
5. [Artifact Templates](standards/ARTIFACTS.md)
6. [Common Standards](standards/common/README.md)
7. [Backend Standards](standards/backend/README.md)
8. [Database Standards](standards/database/README.md)
9. 적용되는 기술 Standards와 Exceptions
10. Backend 환경과 실행 명령

## Frontend Developer

Frontend Developer는 Ready 상태로 승인된 Requirement 범위 안에서 Frontend 코드와 테스트를 구현합니다.

### 책임

- 현재 Requirement의 기능, 화면, 상태, API와 접근성 설계를 읽습니다.
- 공통, Frontend와 선택된 기술 Standards를 적용합니다.
- Frontend 코드, 접근성 동작과 테스트를 구현합니다.
- Requirement에 변경 파일, 구현 요약, 검증 명령과 실제 결과를 기록합니다.
- 접근할 수 있다면 실제 테스트 결과를 Google Sheets 테스트 시나리오 및 결과서에도 반영합니다.
- 공유 계약의 누락, 모호함과 충돌을 Architect에게 에스컬레이션합니다.

### 금지

- Requirement의 명세와 Exceptions를 직접 변경하지 않습니다.
- client 상태나 화면 동작으로 Backend 권한과 Business Rule을 재정의하지 않습니다.
- API 계약에 없는 응답이나 오류를 추측해 영구 구현하지 않습니다.
- 현재 Requirement에 포함되지 않은 Backend 코드나 다른 요구사항을 함께 변경하지 않습니다.
- Standard 규칙을 벗어나는 구현을 승인 없이 추가하지 않습니다.

### 필수 읽기 순서

1. [README.md](README.md)
2. [AGENTS.md](AGENTS.md)
3. 현재 Requirement
4. 참조된 선행 Requirement
5. [Artifact Templates](standards/ARTIFACTS.md)
6. [Common Standards](standards/common/README.md)
7. [Frontend Standards](standards/frontend/README.md)
8. 적용되는 기술 Standards와 Exceptions
9. Frontend 환경과 실행 명령

## 에스컬레이션

Developer는 다음 상황에서 관련 구현을 중단하고 Requirement를 Blocked로 변경합니다.

- 요구사항이나 acceptance criteria가 누락되거나 검증 불가능합니다.
- 기능, 화면, API 또는 Database 설계가 누락되거나 서로 충돌합니다.
- 적용 범위 또는 선행 Requirement가 불명확합니다.
- Standards를 지키면 요구사항을 구현할 수 없습니다.
- 문서화되지 않은 공유 계약이나 아키텍처 결정이 필요합니다.
- 다른 역할의 코드나 완료되지 않은 Requirement에 대한 새로운 의존성이 필요합니다.

Blocked 구역에는 구체적인 사유, 필요한 결정, 영향 범위와 이미 수행한 작업을 기록합니다. Architect가 명세를 갱신하거나 Exception을 작성한 뒤 Requirement를 Ready로 전환합니다.

## 반복 운영

1. Architect가 다음 사용자 결과를 하나의 Requirement로 생성합니다.
2. 요구사항, 기능 명세, 화면 설계, Database 설계와 테스트 계획을 순서대로 확정하고 대응하는 Google Sheets와 Figma 산출물을 함께 갱신합니다.
3. Ready 기준을 확인하고 구현 역할을 지정합니다.
4. Developer가 In Progress로 전환하고 코드와 테스트를 작성합니다.
5. Developer가 실제 테스트 결과를 Requirement와 Google Sheets 테스트 결과서에 기록하고 Review로 전환합니다.
6. Architect가 명세, 코드와 결과를 통합 검토해 Done으로 승인합니다.
7. 다음 Requirement에서 같은 과정을 반복합니다.

각 컨텍스트는 다른 컨텍스트의 대화가 아니라 저장소에 기록된 Requirement 상태와 내용을 통해 협업합니다.
