# Frontend Standards

## 목적

`standards/frontend/`는 Frontend 기술에 공통으로 적용되는 API 사용, UI 상태, 접근성과 client 보안 규칙을 정의합니다.

## 문서

| 문서 | 내용 |
| --- | --- |
| `FE-01-api-client-convention.md` | API 계약, 인증과 오류 |
| `FE-02-api-request-lifecycle-convention.md` | 요청 취소, 중복 제출과 mock |
| `FE-03-ui-convention.md` | 디자인 token, 상호작용과 접근성 |
| `FE-04-responsive-content-convention.md` | 반응형 콘텐츠와 animation |
| `react/` | React와 TypeScript를 선택한 프로젝트의 구현 규칙 |

Frontend 작업은 이 디렉터리의 공통 규칙을 먼저 적용하고, Customs에서 React를 선택한 경우 `react/` 규칙을 함께 적용합니다.
