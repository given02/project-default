# Workflow

## 목적

`standards/workflow/`는 모든 프로젝트에서 공통으로 사용할 시작 절차와 산출물 운영 방식을 정의합니다.

```text
start
→ 프로젝트와 산출물 링크 초기화
→ Requirement 정의
→ 산출물 갱신
→ 코드와 테스트
→ 테스트 결과 갱신
→ 다음 Requirement 반복
```

## 영역 경계

| 영역 | 소유하는 내용 |
| ---- | ------------- |
| `standards/workflow/` | 프로젝트 시작, 질문, 산출물 생성과 동기화 절차 |
| `standards/common/`, `backend/`, `frontend/`, `database/` | 코드, 아키텍처, 테스트와 기술별 구현 규칙 |
| `customs/` | 현재 프로젝트의 요구사항, 설계, 상태, 구현과 검증 결과 |
| `exceptions/` | Standards를 벗어나는 현재 적용 예외 |

Workflow는 프로젝트별 값이나 제품 의미를 소유하지 않습니다. 프로젝트 설명, 산출물 링크와 실제 결정은 `customs/`에 기록합니다.

## 문서

- [Start Prompt](start.md): 사용자가 `start`를 입력했을 때 실행할 초기 질문과 후속 절차
- [Artifact Templates](artifacts.md): 요구사항, 기능, 화면, Database와 테스트 산출물 생성 규격

## 변경 권한

clone으로 생성한 실제 프로젝트에서는 `standards/workflow/`를 읽기 전용으로 사용합니다. 공통 Workflow 변경은 `project-default`에서 새 버전으로 배포합니다.

프로젝트별로 산출물이 적용되지 않으면 Workflow를 수정하지 않고 `customs/PROJECT.md`와 관련 Requirement에 `해당 없음`, 이유와 재검토 조건을 기록합니다.

## 읽기 순서

1. 프로젝트를 시작할 때 `start.md`
2. 외부 산출물을 생성하거나 갱신할 때 `artifacts.md`
3. 현재 작업의 Requirement와 관련 Standards 및 Exceptions
