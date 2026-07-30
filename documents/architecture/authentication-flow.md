# 인증 및 인가 흐름

- Owner: Architect
- Purpose: 프로젝트가 인증을 사용할 경우의 공유 흐름을 정의합니다.
- Audience: 모든 역할
- Dependencies: `architecture.md`, `../api/api-contract.md`
- Next Reading: `../api/api-contract.md`

## 적용 여부

{{AUTH_REQUIRED_OR_NOT}}

인증을 사용하지 않는 프로젝트는 이유와 향후 재검토 조건을 기록하고 아래 선택 항목을 제거할 수 있습니다.

## 인증 방식

- 사용자 식별 방식: {{IDENTITY_METHOD}}
- 자격 증명 또는 외부 IdP: {{CREDENTIAL_OR_IDP}}
- 세션 또는 토큰 방식: {{SESSION_OR_TOKEN}}
- 클라이언트 저장 및 전송: {{CLIENT_HANDLING}}
- 만료와 갱신: {{EXPIRATION_AND_REFRESH}}

## 흐름

1. {{AUTH_FLOW_STEP}}
2. {{AUTH_FLOW_STEP}}

## 인가

- 역할 또는 권한 모델: {{AUTHORIZATION_MODEL}}
- 리소스 소유권 검증: {{OWNERSHIP_RULE}}

## 실패 계약

- 인증 및 인가 오류는 `../api/api-response.md`를 따릅니다.
