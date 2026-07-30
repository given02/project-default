# 거버넌스

- Owner: Architect
- Purpose: 프로젝트의 소유권, 검토, 승인과 에스컬레이션 절차를 정의합니다.
- Audience: 모든 역할
- Dependencies: `../AGENTS.md`
- Next Reading: `git-convention.md`

## 소유권

공유 프로젝트 지식은 Architect가 소유합니다. Backend와 Frontend는 공유 지식을 참조하지만 로컬 문서에서 재정의하지 않습니다.

## 에스컬레이션 절차

공유 문서에 누락, 모호함 또는 충돌이 있으면:

1. 관련 구현을 멈춥니다.
2. 구현에서 의미를 추측하거나 재정의하지 않습니다.
3. Architect에게 문제와 필요한 결정을 전달합니다.
4. Architect가 적절한 source-of-truth 문서를 갱신합니다.
5. 문서 검토 후 구현을 재개합니다.

## 결정 권한

- Architect는 팀 간 결정과 공유 문서 변경을 승인합니다.
- Backend와 Frontend는 공유 의미를 바꾸지 않는 역할 내부 기술 결정을 승인합니다.
- 되돌리기 어렵거나 여러 컴포넌트에 영향을 주는 결정은 ADR을 요구합니다.

## 변경 정책

- 문서화된 동작이 바뀌면 같은 작업에서 문서를 갱신합니다.
- 같은 개념을 복사하지 않고 기존 source of truth를 링크합니다.
- 문서와 구현이 충돌하면 원인을 확인하고 명시적으로 정렬합니다.
