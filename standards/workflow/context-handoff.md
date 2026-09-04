# Context Handoff

## 목적

하나의 Requirement를 명세하는 Architect와 구현하는 Developer가 서로 다른 Codex 컨텍스트에서 작업하도록 분리합니다. 고성능 모델은 제품 의미와 승인에 집중하고, 비용 효율 모델은 범위가 확정된 구현과 테스트에 집중합니다.

```text
Architect 주 컨텍스트
Draft → Ready
        ↓
Developer Agent 컨텍스트
In Progress → Review
        ↓
기존 Architect 주 컨텍스트
Review → Ready 또는 Done
```

Requirement와 저장소 파일이 컨텍스트 사이의 source of truth입니다. 다른 컨텍스트의 대화 내용이나 기억은 인수인계 조건으로 사용하지 않습니다.

## 컨텍스트와 모델

| 컨텍스트 | 책임 | 기본 모델 정책 |
| -------- | ---- | ---------------- |
| Architect 주 컨텍스트 | Requirement 명세, `Ready` 승인, 구현 통합 검토와 `Done` 승인 | 사용 가능한 최신 고성능 모델, reasoning `high` 이상 |
| Backend Developer Agent | Ready Requirement의 Backend 코드와 테스트, 결과 기록과 `Review` 전환 | `.codex/agents/backend-developer.toml` |
| Frontend Developer Agent | Ready Requirement의 Frontend 코드와 테스트, 결과 기록과 `Review` 전환 | `.codex/agents/frontend-developer.toml` |

- 사용자는 새 프로젝트 작업을 시작할 때 Architect 주 컨텍스트의 모델을 직접 선택합니다.
- Agent 설정 파일은 현재 템플릿 버전의 기본값입니다. 사용할 수 없는 모델이면 임의 모델로 조용히 대체하지 않고 사용자에게 선택을 요청합니다.
- Developer 모델은 명세가 완결된 범위의 구현을 전제로 합니다. 제품 의미를 새로 결정해야 하면 구현하지 않고 `Blocked`로 전환합니다.
- 하나의 컨텍스트는 실행 중 역할을 바꾸지 않습니다.

## 실행 절차

### 1. Architect 컨텍스트

1. Architect가 사용자와 Requirement의 요구사항, 기능, 화면, Database와 테스트 계획을 확정합니다.
2. 외부 산출물을 동기화하고 Ready 기준을 검토합니다.
3. 기준을 충족하면 Requirement를 `Ready`로 전환하고 다음 구현 역할을 `실행 소유권`에 지정합니다.
4. 구현을 계속하라는 사용자 요청이 있으면 지정된 Developer Agent에 Requirement ID 하나를 전달해 순차적으로 위임합니다.
5. Architect는 Developer가 `Review` 또는 `Blocked`로 전환할 때까지 같은 Requirement의 production code를 수정하지 않습니다.

### 2. Developer Agent 컨텍스트

1. Developer는 `AGENTS.md`의 역할별 읽기 순서와 지정된 Requirement를 읽습니다.
2. Requirement가 `Ready`이고 `실행 소유권`의 다음 역할이 자신과 일치하는지 확인합니다. 하나라도 일치하지 않으면 파일을 수정하지 않고 Architect에게 반환합니다.
3. production code를 수정하기 전에 상태를 `In Progress`로 전환하고 실행 소유권에 자신의 역할, Agent 이름, 시작 시각과 변경 예상 영역을 기록합니다. 이 변경이 작업 점유입니다.
4. 상태 변경 직후 다시 Requirement를 읽어 자신의 점유가 유지되는지 확인합니다. 다른 작업자가 먼저 점유했거나 내용이 충돌하면 구현하지 않고 종료합니다.
5. 명세 누락이나 충돌을 발견하면 추측하지 않고 `Blocked` 사유를 기록한 뒤 종료합니다.
6. 구현과 검증이 완료되면 실제 결과와 완료 시각을 기록하고 `Review`로 전환한 뒤 Architect에게 요약을 반환합니다.

### 3. Architect 검토

1. 기존 Architect 컨텍스트가 Requirement, diff, 테스트 결과와 외부 산출물 반영 상태를 검토합니다.
2. 다음 구현 역할이 남아 있으면 완료된 역할을 기록하고 다음 역할을 실행 소유권에 지정한 뒤 `Ready`로 전환합니다.
3. 모든 구현 역할이 완료되고 명세와 구현이 일치하면 `Done`으로 승인합니다.
4. 구현 수정만 필요하면 담당 역할을 다시 지정하고 `Ready`로 전환해 같은 Developer 역할에 재위임합니다.
5. 명세 결정이 필요하면 `Blocked` 내용을 해결하고 명세와 테스트 계획을 갱신한 뒤 다시 `Ready`로 승인합니다.

## 위임 프롬프트

Backend 구현:

```text
backend_developer Agent로 REQ-001을 구현하세요.
Ready 상태와 범위를 먼저 확인하고 AGENTS.md의 Backend Developer 읽기 순서를 따르세요.
명세를 변경하거나 추측하지 말고, 모호하면 Blocked로 전환하세요.
구현과 테스트 결과를 기록한 뒤 Review로 전환하고 변경 및 검증 요약만 반환하세요.
```

Frontend 구현:

```text
frontend_developer Agent로 REQ-001을 구현하세요.
Ready 상태와 범위를 먼저 확인하고 AGENTS.md의 Frontend Developer 읽기 순서를 따르세요.
명세를 변경하거나 추측하지 말고, 모호하면 Blocked로 전환하세요.
구현과 테스트 결과를 기록한 뒤 Review로 전환하고 변경 및 검증 요약만 반환하세요.
```

## 병렬 작업 제한

- Architect는 Requirement 하나에 한 번에 하나의 다음 구현 역할만 지정하고 Developer Agent 하나만 실행합니다.
- `Ready`인 Requirement만 점유할 수 있으며, 먼저 `In Progress`로 전환하고 실행 소유권을 기록한 Developer만 구현 파일을 변경할 수 있습니다.
- 다른 Agent는 Requirement가 `In Progress`이면 실행 소유권의 변경 예상 영역과 관계없이 해당 Requirement의 모든 파일을 변경하지 않습니다.
- Backend와 Frontend가 같은 Requirement를 구현하면 Architect가 공유 API 계약과 순서를 정하고 기본적으로 순차 실행합니다.
- 완전히 독립된 Requirement도 사용자가 병렬 실행을 요청하지 않으면 순차 실행합니다.
- 탐색, 테스트 로그 분석처럼 쓰기 작업이 없는 보조 작업만 필요에 따라 병렬화할 수 있습니다.
- 토큰 절감이 목적이므로 Developer가 다시 읽을 자료는 현재 Requirement, 참조된 선행 Requirement와 적용되는 Standards 및 Exceptions로 제한합니다.
