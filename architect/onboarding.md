# 온보딩

- Owner: Architect
- Purpose: 신규 기여자와 Codex 컨텍스트의 시작 절차를 정의합니다.
- Audience: 모든 역할
- Dependencies: `../README.md`, `../codex/README.md`
- Next Reading: `bootstrapping.md`

## 핵심 규칙

이전 대화는 필수 맥락이 아닙니다. 저장소 문서가 유일한 온보딩 source입니다.

## 최초 프로젝트 설정

1. `../codex/MASTER_PROMPT.md`를 사용해 문서 기준선을 검토합니다.
2. 모든 `{{...}}` 플레이스홀더를 프로젝트 값으로 교체합니다.
3. 요구사항, 도메인 모델, 아키텍처와 API 계약을 작성합니다.
4. 불필요한 선택 문서를 제거하거나 `해당 없음`으로 기록합니다.
5. `review-checklist.md`로 검토합니다.
6. 초기 결정을 `decision-log.md`와 ADR에 기록합니다.
7. 기준선 승인 후 기능 개발을 시작합니다.

## 이후 Architect 세션

1. `../codex/ARCHITECT_PROMPT.md`를 사용합니다.
2. `../AGENTS.md`의 읽기 순서를 따릅니다.

## 이후 Backend 세션

1. `../codex/BACKEND_PROMPT.md`를 사용합니다.
2. `../Backend/AGENTS.md`의 읽기 순서를 따릅니다.

## 이후 Frontend 세션

1. `../codex/FRONTEND_PROMPT.md`를 사용합니다.
2. `../Frontend/AGENTS.md`의 읽기 순서를 따릅니다.
