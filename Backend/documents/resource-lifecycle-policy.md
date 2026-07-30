# Resource Lifecycle Policy

- Owner: Backend Developer
- Purpose: 리소스별 생성, 조회, 수정, 삭제 구현 정책을 기록합니다.
- Audience: Backend Developer
- Dependencies: `../../documents/product/business-rule.md`, `persistence-convention.md`

## {{RESOURCE_NAME}}

| 동작 | 정책 | 관련 비즈니스 규칙 |
| --- | --- | --- |
| Create | {{CREATE_POLICY}} | `BR-{{NUMBER}}` |
| Read | {{READ_POLICY}} | `BR-{{NUMBER}}` |
| Update | {{UPDATE_POLICY}} | `BR-{{NUMBER}}` |
| Delete | Soft delete | Hard delete | Archive | Unsupported |

## 삭제와 보존

- 보존 기간: {{RETENTION_POLICY}}
- 연관 데이터 처리: {{CASCADE_OR_PRESERVE_POLICY}}
- 복구 가능 여부: {{RECOVERY_POLICY}}
- 개인정보 삭제 요구: {{PRIVACY_DELETION_POLICY_OR_NONE}}

이 문서는 제품 규칙을 새로 만들지 않고 공유 비즈니스 규칙의 persistence 구현만 설명합니다.
