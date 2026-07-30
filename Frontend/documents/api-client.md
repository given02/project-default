# API Client

- Owner: Frontend Developer
- Purpose: API 호출, type, 인증과 오류 처리 구현 규칙을 정의합니다.
- Audience: Frontend Developer
- Dependencies: `../../documents/api/api-contract.md`, `../../documents/api/api-response.md`
- Next Reading: `ui-convention.md`

## Client

- Library: {{HTTP_CLIENT_OR_FETCH}}
- Base URL 설정: {{BASE_URL_CONFIGURATION}}
- Timeout: {{TIMEOUT_POLICY}}
- Retry: {{RETRY_POLICY}}

## 규칙

- API 함수는 feature 또는 resource 단위로 구성합니다.
- 요청과 응답 type은 공유 API 계약을 따릅니다.
- HTTP 성공 여부와 domain 응답 성공 여부를 계약에 맞게 구분합니다.
- 오류는 사용자가 이해할 메시지와 개발 진단 정보를 분리합니다.
- 인증 정보 전송 방식은 공유 인증 흐름을 따릅니다.
- request 취소와 stale response 처리 방식을 정의합니다.
- mock 응답이 실제 계약과 분기되지 않도록 관리합니다.
