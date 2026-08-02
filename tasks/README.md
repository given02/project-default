# Tasks

## 목적

`tasks/`는 현재 프로젝트에서 실행할 구현 작업을 관리합니다.

각 Task는 이미 정의된 프로젝트 명세를 한 Agent가 구현하고 검증할 수 있는 범위로 제한합니다. Task에는 작업 목표, 참조 항목, 구현 범위, 제외 범위, 완료 조건과 검증 방법을 기록합니다.

Agent 역할과 변경 권한은 [AGENTS.md](../AGENTS.md)를 따릅니다. Task는 [Customs](../customs/README.md)에 정의된 프로젝트 의미를 참조하고, 적용되는 예외가 있으면 [Exceptions](../exceptions/README.md)의 Exception ID를 연결합니다.

## 파일 이름

Task 파일은 다음 형식을 사용합니다.

```text
tsk-<3자리 번호>-<영문 이름>.md
```

예:

```text
tsk-001-bootstrap-backend.md
tsk-002-bootstrap-frontend.md
tsk-003-user-registration-api.md
tsk-004-user-registration-screen.md
```

- 번호는 `001`부터 순차 증가합니다.
- 파일 이름은 lowercase kebab-case를 사용합니다.
- 제거된 Task 번호를 다른 작업에 재사용하지 않습니다.
- 제목이나 파일 이름이 바뀌어도 같은 Task는 기존 ID를 유지합니다.
- 하나의 파일은 하나의 명확한 작업 목적만 소유합니다.

## Task ID

Task ID는 다음 형식을 사용합니다.

```text
TSK-001
```

파일 `tsk-001-*`와 ID `TSK-001`의 번호는 일치해야 합니다.

다른 문서와 Task는 파일 이름 대신 Task ID로 선행 관계와 관련 작업을 참조합니다.

## Task 분리

하나의 Task는 한 역할이 독립적으로 실행하고 검증할 수 있어야 합니다.

- Backend와 Frontend 구현은 별도 Task로 분리합니다.
- 프로젝트 초기화와 production 기능 구현을 분리합니다.
- 문서 결정과 코드 구현을 하나의 Task에 섞지 않습니다.
- 서로 독립적으로 되돌려야 하는 변경은 별도 Task로 분리합니다.
- 선행 작업이 필요하면 Task ID로 의존성을 기록합니다.
- 하나의 Task가 지나치게 커지면 사용자에게 확인 가능한 결과 단위로 나눕니다.
- 단순히 파일 수가 많다는 이유만으로 같은 목적의 변경을 불필요하게 분리하지 않습니다.

## Task 종류

### Bootstrap

프로젝트 구조와 실행 기반을 생성합니다.

예:

- Backend 프로젝트 생성
- Frontend 프로젝트 생성
- Database와 migration 기반 구성
- formatter, lint, test와 build 구성

### Backend

Backend 코드, migration과 테스트를 구현합니다.

예:

- use case와 domain 동작
- API endpoint
- persistence와 외부 연동
- Database migration

### Frontend

Frontend 화면, 상태, API 연동과 테스트를 구현합니다.

예:

- route와 page
- feature와 component
- form과 validation
- loading, empty, error와 success 상태

### Integration

이미 구현된 Backend와 Frontend의 계약과 end-to-end 동작을 검증합니다.

Integration Task는 누락된 제품 의미를 새로 결정하지 않습니다. 계약 변경이 필요하면 구현을 진행하기 전에 관련 명세를 먼저 갱신합니다.

## 상태

Task는 다음 상태 중 하나를 가집니다.

```text
Draft
Ready
In Progress
Blocked
Review
Done
Cancelled
```

### Draft

작업 범위와 완료 조건을 작성 중입니다. 구현을 시작하지 않습니다.

### Ready

필요한 참조 문서, 선행 Task, 범위와 검증 방법이 준비되었습니다. 할당된 Agent가 작업을 시작할 수 있습니다.

### In Progress

할당된 Agent가 구현과 검증을 수행하고 있습니다.

### Blocked

누락된 결정, 문서 충돌, 선행 작업 또는 외부 조건으로 인해 진행할 수 없습니다. Blocked 사유와 필요한 해결 내용을 Task에 기록합니다.

### Review

구현과 검증이 끝났으며 Architect의 통합 검토를 기다리고 있습니다.

### Done

구현, 테스트와 검토가 완료되었습니다. Task 파일을 Done 상태로 유지합니다.

### Cancelled

작업이 더 이상 필요하지 않습니다. 취소 이유와 영향을 기록하고 Task 파일을 Cancelled 상태로 유지합니다.

## 상태 전이

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

Review에서 변경이 필요하면 Task를 In Progress로 되돌리고 검토 내용을 기록합니다.

## 필수 내용

각 Task 파일은 다음 형식을 사용합니다.

```markdown
# TSK-001: 작업 제목

## 상태

Draft

## 할당 역할

Backend Developer | Frontend Developer | Architect

## 목표

작업이 완료되었을 때 달성해야 하는 결과

## 참조 항목

- Requirement ID:
- Business Rule ID:
- Flow ID:
- Screen ID:
- API ID:
- Exception ID:

## 선행 Task

- `TSK-번호` 또는 해당 없음

## 구현 범위

- 이번 Task에서 변경할 동작

## 제외 범위

- 이번 Task에서 의도적으로 변경하지 않을 내용

## 완료 조건

- 외부에서 확인할 수 있는 결과
- 충족해야 하는 acceptance criteria

## 검증

- 실행할 formatter, lint, test와 build 명령
- 필요한 수동 또는 end-to-end 검증

## Blocked

- 사유:
- 필요한 결정 또는 선행 작업:

## 구현 결과

- 구현 요약:
- 변경 파일:
- migration 또는 생성 파일:

## 검증 결과

- 실행한 명령:
- 결과:
- 실행하지 못한 검증과 이유:

## 검토 결과

- 검토 내용:
- 남은 작업:
```

적용되지 않는 항목에는 `해당 없음`과 이유를 기록합니다.

## 참조 규칙

- Task는 프로젝트 명세의 내용을 복사하지 않고 관련 ID를 참조합니다.
- Task에 새로운 요구사항, 비즈니스 규칙, 화면, API 또는 Database 의미를 정의하지 않습니다.
- 적용할 Standard 전체를 나열하지 않고 작업과 직접 관련된 규칙 ID만 필요한 경우 기록합니다.
- Exception이 적용되면 Exception ID를 명시합니다.
- 선행 Task가 완료되지 않았으면 현재 Task를 Ready로 전환하지 않습니다.

## Blocked 처리

Task를 Blocked로 전환할 때 다음을 기록합니다.

- 진행할 수 없는 구체적인 이유
- 누락되거나 충돌하는 문서와 ID
- 필요한 결정
- 영향을 받는 구현 범위
- 이미 수행한 작업과 검증

문제가 해결되면 해결 내용을 관련 문서에 먼저 반영하고 Task의 Blocked 항목에 해결 근거를 기록한 뒤 Ready로 전환합니다.

## 완료 조건

Task를 Review로 전환하기 전에 다음을 확인합니다.

- 구현이 Task의 목표와 범위를 충족합니다.
- 제외 범위를 의도치 않게 변경하지 않았습니다.
- 관련 acceptance criteria가 충족됩니다.
- 필요한 코드, test와 migration이 함께 작성되었습니다.
- formatter, lint, test와 build 검증 결과가 기록되었습니다.
- 실행하지 못한 검증과 이유가 기록되었습니다.
- 구현 중 발견한 누락과 충돌이 해결되었습니다.
- 구현 결과와 변경 파일이 Task에 기록되었습니다.

Task를 Done으로 전환하기 전에 검토 결과와 남은 작업이 정리되어 있어야 합니다.

## 완료 Task 보존

- Done 또는 Cancelled Task 파일을 삭제하지 않습니다.
- 완료된 Task의 범위, 구현 결과와 검증 증거를 파일에 유지합니다.
- Task ID는 다른 작업에 재사용하지 않습니다.
- 현재 실행할 작업은 각 Task 파일의 상태로 확인합니다.
- 별도의 Task Index를 관리하지 않습니다.
