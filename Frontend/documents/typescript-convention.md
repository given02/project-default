# TypeScript Convention

- Owner: Frontend Developer
- Purpose: TypeScript type와 안전성 규칙을 정의합니다.
- Audience: Frontend Developer
- Dependencies: `frontend-convention.md`, `../../documents/api/api-contract.md`
- Next Reading: `routing.md`

## 규칙

- strict mode를 기본으로 사용합니다.
- `any`보다 `unknown`, generic 또는 구체적인 type을 사용합니다.
- API type은 문서화된 계약과 일치시킵니다.
- nullable과 optional의 의미를 구분합니다.
- domain 상태는 가능한 경우 discriminated union으로 유효한 상태만 표현합니다.
- type assertion은 runtime 검증 또는 명확한 근거가 있을 때만 사용합니다.
- enum, union과 상수의 선택 기준을 프로젝트 전체에서 일관되게 유지합니다.

## 생성 코드

OpenAPI 등에서 type을 생성하는 경우:

- 생성 명령: `{{TYPE_GENERATION_COMMAND}}`
- 생성 파일 위치: `{{GENERATED_TYPE_LOCATION}}`
- 생성 파일 직접 수정 여부: {{EDIT_POLICY}}
