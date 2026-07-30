# 의존성 규칙

- Owner: Architect
- Purpose: 프로젝트 수준 의존성 방향과 협업 경계를 정의합니다.
- Audience: 모든 역할
- Dependencies: `architecture.md`, `domain-model.md`
- Next Reading: `authentication-flow.md`

## 프로젝트 수준 규칙

- 프로젝트 의미는 Architect 공유 문서에서 역할별 구현으로 흐릅니다.
- 각 컴포넌트는 문서화된 인터페이스를 통해 통신합니다.
- 소비자는 다른 컴포넌트의 내부 구현이나 persistence 모델에 의존하지 않습니다.
- 순환 의존성을 만들지 않습니다.
- 새 공유 의존성이나 계약이 필요하면 구현 전에 Architect에게 에스컬레이션합니다.

## 허용 의존성

| 출발 | 도착 | 허용 여부 | 계약 |
| --- | --- | --- | --- |
| {{SOURCE_COMPONENT}} | {{TARGET_COMPONENT}} | 허용 | {{DOCUMENTED_INTERFACE}} |
