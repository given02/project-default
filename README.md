# {{PROJECT_NAME}}

## 목적

{{PROJECT_SUMMARY}}

이 저장소는 문서를 source of truth로 사용하며, 서로 독립적인 작업 컨텍스트가 이전 대화 없이도 개발을 이어갈 수 있도록 구성합니다.

## 프로젝트 구성

- `codex/`: 역할별 Codex 컨텍스트 초기화 지침
- `architect/`: 거버넌스, 온보딩, 계획, 의사결정
- `documents/`: 제품, 아키텍처, API, 용어집, ADR 등 공유 문서
- `Backend/`: Backend 구현과 Backend 전용 규칙
- `Frontend/`: Frontend 구현과 Frontend 전용 규칙

## 읽는 순서

1. `codex/README.md`
2. `architect/onboarding.md`
3. 자신의 역할에 맞는 `AGENTS.md`
4. 역할별 읽기 순서에 포함된 문서

## 개발 모델

프로젝트는 Architect, Backend Developer, Frontend Developer 역할로 개발합니다.

- Architect는 제품 방향, 요구사항, 비즈니스 규칙, 도메인 모델, 아키텍처, API 계약, 용어집, ADR, 거버넌스를 소유합니다.
- Backend Developer는 공유 문서가 정한 경계 안에서 Backend 구현과 전용 규칙을 소유합니다.
- Frontend Developer는 공유 문서가 정한 경계 안에서 Frontend 구현과 전용 규칙을 소유합니다.

문서와 구현이 충돌하면 Architect가 문서를 명시적으로 갱신하기 전까지 문서가 우선합니다.

## 템플릿 사용 방법

1. 이 디렉터리의 내용을 새 프로젝트 루트로 복사합니다.
2. `{{...}}` 형식의 플레이스홀더를 프로젝트 값으로 교체합니다.
3. 적용하지 않는 선택 항목은 삭제하거나 `해당 없음`으로 결정 기록을 남깁니다.
4. `architect/review-checklist.md`로 초기 문서 정합성을 검토합니다.
5. 거버넌스를 승인한 뒤 기능 개발을 시작합니다.
