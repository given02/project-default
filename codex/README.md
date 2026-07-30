# Codex

## 목적

역할별 Codex 컨텍스트를 저장소 문서에 연결하는 최소 진입점을 제공합니다. 프롬프트는 초기화 수단이며, 지속적인 프로젝트 지식의 source of truth는 저장소 문서입니다.

## 프롬프트

- `MASTER_PROMPT.md`: 템플릿을 새 프로젝트에 적용하고 기준선을 수립할 때 사용
- `ARCHITECT_PROMPT.md`: Architect 작업 컨텍스트 초기화
- `BACKEND_PROMPT.md`: Backend 작업 컨텍스트 초기화
- `FRONTEND_PROMPT.md`: Frontend 작업 컨텍스트 초기화
- `VERSION.md`: 템플릿 또는 거버넌스 버전 기록

## 사용 규칙

- 컨텍스트 하나에는 역할 프롬프트 하나만 사용합니다.
- 프롬프트 실행 후 해당 역할의 `AGENTS.md` 읽기 순서를 따릅니다.
- 프롬프트에 제품 요구사항이나 지속적인 기술 결정을 추가하지 않습니다.
- 중요한 작업 결과는 적절한 source-of-truth 문서에 기록합니다.

## 최초 설정

1. `MASTER_PROMPT.md`를 사용합니다.
2. 모든 플레이스홀더와 선택 항목을 검토합니다.
3. `../architect/review-checklist.md`를 통과시킵니다.
4. 초기 거버넌스와 아키텍처 결정을 승인합니다.

## 이후 세션

- Architect: `ARCHITECT_PROMPT.md`
- Backend: `BACKEND_PROMPT.md`
- Frontend: `FRONTEND_PROMPT.md`
