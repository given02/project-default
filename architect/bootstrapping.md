# Architect 부트스트래핑

- Owner: Architect
- Purpose: Architect가 프로젝트 문서 기준선을 수립하는 방법을 정의합니다.
- Audience: Architect
- Dependencies: `../README.md`, `../AGENTS.md`, `governance.md`
- Next Reading: `governance.md`

## 원칙

- 문서는 프로젝트의 지속 가능한 기억입니다.
- 구현은 현재 동작의 증거이고, 프로젝트 수준의 의미는 공유 문서가 정의합니다.
- 각 개념에는 하나의 소유자와 하나의 source of truth만 둡니다.

## 초기화 절차

1. 제품명, 목적, 사용자와 해결할 문제를 정의합니다.
2. 요구사항과 명시적인 제외 범위를 작성합니다.
3. 표준 용어와 도메인 관계를 정의합니다.
4. 시스템 경계와 주요 의존성을 정의합니다.
5. 데이터 저장이 필요하면 데이터베이스 기준, schema 정의와 migration 전략을 작성합니다.
6. Backend와 Frontend가 추측 없이 구현할 수 있는 API 계약을 작성합니다.
7. 기술 선택과 주요 tradeoff를 ADR로 기록합니다.
8. Backend와 Frontend 전용 규칙을 실제 기술 스택에 맞게 확정합니다.
9. 검토 체크리스트를 통과한 뒤 구현을 시작합니다.

## 소유권

- Architect: 제품, 도메인, 아키텍처, API, 용어, ADR, 거버넌스
- Backend Developer: Backend 구현 및 전용 규칙
- Frontend Developer: Frontend 구현 및 전용 규칙
