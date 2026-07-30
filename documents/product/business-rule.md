# 비즈니스 규칙

- Owner: Architect
- Purpose: 구현 기술과 독립적인 제품 규칙과 invariant를 정의합니다.
- Audience: 모든 역할
- Dependencies: `requirements.md`, `../architecture/domain-model.md`
- Next Reading: `../architecture/domain-model.md`

## 규칙

### BR-001: {{RULE_NAME}}

- 설명: {{RULE_DESCRIPTION}}
- 적용 대상: {{AFFECTED_DOMAIN}}
- 조건: {{CONDITION}}
- 결과: {{OUTCOME}}
- 예외: {{EXCEPTIONS_OR_NONE}}
- 검증 예시: {{VERIFIABLE_EXAMPLE}}
- 관련 요구사항: `REQ-{{NUMBER}}`

## 정책

- 비즈니스 규칙은 이 문서 또는 연결된 Architect 소유 문서에만 정의합니다.
- Backend와 Frontend는 규칙을 구현하지만 의미를 재정의하지 않습니다.
- 규칙 변경은 관련 요구사항, 도메인 모델, API와 테스트 영향을 함께 검토합니다.
