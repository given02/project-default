# API 응답 정책

- Owner: Architect
- Purpose: 공통 성공 및 실패 응답 형식을 정의합니다.
- Audience: Backend Developer와 Frontend Developer
- Dependencies: `api-contract.md`
- Next Reading: `../product/requirements.md`

## 응답 전략

다음 중 프로젝트가 사용할 방식을 결정하고 나머지는 제거합니다.

- 표준 HTTP status와 리소스 body를 직접 사용
- 공통 envelope 사용
- RFC 9457 Problem Details를 오류 응답에 사용

선택: {{RESPONSE_STRATEGY}}

## 성공 응답

- 생성: {{CREATE_STATUS_AND_BODY}}
- 조회: {{READ_STATUS_AND_BODY}}
- 수정: {{UPDATE_STATUS_AND_BODY}}
- 삭제: {{DELETE_STATUS_AND_BODY}}

## 오류 응답

```json
{
  "code": "{{STABLE_ERROR_CODE}}",
  "message": "{{SAFE_MESSAGE}}",
  "details": {}
}
```

| 오류 코드 | HTTP Status | 의미 | 클라이언트 동작 |
| --- | --- | --- | --- |
| `{{ERROR_CODE}}` | `{{STATUS}}` | {{MEANING}} | {{CLIENT_ACTION}} |

## 규칙

- 내부 예외, stack trace와 민감정보를 응답에 노출하지 않습니다.
- 오류 코드는 클라이언트가 분기할 수 있도록 안정적으로 유지합니다.
- validation 오류의 필드 표현을 프로젝트 전체에서 일관되게 유지합니다.
