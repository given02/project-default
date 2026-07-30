# API 계약

- Owner: Architect
- Purpose: 서비스 소비자와 제공자가 함께 따르는 API 계약을 정의합니다.
- Audience: Backend Developer와 Frontend Developer
- Dependencies: `../architecture/domain-model.md`, `api-response.md`
- Next Reading: `api-response.md`

## 공통 규칙

- Base URL: `{{API_BASE_URL}}`
- Content-Type: `{{DEFAULT_CONTENT_TYPE}}`
- 인증: `{{AUTH_REQUIREMENT_OR_NONE}}`
- 날짜 및 시간: `{{DATE_TIME_FORMAT_AND_TIMEZONE}}`
- Pagination: `{{PAGINATION_POLICY_OR_NONE}}`
- Versioning: `{{VERSIONING_POLICY}}`

## {{RESOURCE_NAME}} API

### {{OPERATION_NAME}}

| 항목 | 값 |
| --- | --- |
| Method | `{{HTTP_METHOD}}` |
| Path | `{{PATH}}` |
| 인증 | {{AUTH_REQUIRED}} |
| 권한 | {{AUTHORIZATION_RULE_OR_NONE}} |
| 성공 상태 | `{{SUCCESS_STATUS}}` |

#### Path Parameter

| 이름 | 타입 | 필수 | 설명 |
| --- | --- | --- | --- |
| `{{NAME}}` | `{{TYPE}}` | 예 | {{DESCRIPTION}} |

#### Query Parameter

| 이름 | 타입 | 필수 | 기본값 | 설명 |
| --- | --- | --- | --- | --- |
| `{{NAME}}` | `{{TYPE}}` | 아니요 | `{{DEFAULT}}` | {{DESCRIPTION}} |

#### Request

```json
{
  "{{field}}": "{{value}}"
}
```

#### Response

```json
{
  "{{field}}": "{{value}}"
}
```

#### 오류

| 조건 | HTTP Status | 오류 코드 |
| --- | --- | --- |
| {{FAILURE_CONDITION}} | `{{STATUS}}` | `{{ERROR_CODE}}` |

#### 관련 요구사항

- `REQ-{{NUMBER}}`
