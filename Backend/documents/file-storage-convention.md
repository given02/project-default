# File Storage Convention

- Owner: Backend Developer
- Purpose: 파일 저장 기능을 사용할 경우의 Backend 구현 규칙을 정의합니다.
- Audience: Backend Developer
- Dependencies: `project-environment.md`, `../../documents/product/business-rule.md`

## 적용 여부

{{FILE_STORAGE_REQUIRED_OR_NOT}}

## 설정

- Provider: {{STORAGE_PROVIDER}}
- Local development: {{LOCAL_STORAGE_STRATEGY}}
- Object key 규칙: {{OBJECT_KEY_RULE}}
- 공개/비공개 정책: {{ACCESS_POLICY}}
- URL 제공 방식: {{URL_OR_SIGNED_URL_POLICY}}

## 검증

- 허용 content type: {{ALLOWED_CONTENT_TYPES}}
- 최대 크기: {{MAX_FILE_SIZE}}
- 악성 파일 검사: {{MALWARE_SCAN_POLICY}}

## 생명주기

- 업로드와 metadata transaction 처리: {{CONSISTENCY_STRATEGY}}
- 교체: {{REPLACEMENT_POLICY}}
- 삭제와 보존: {{DELETION_POLICY}}

## 보안

- credential을 코드나 설정 파일에 hard-code하지 않습니다.
- 사용자 제공 파일명으로 object key 또는 filesystem path를 직접 만들지 않습니다.
- private file 접근에는 권한 검증을 적용합니다.
