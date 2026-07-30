# Routing

- Owner: Frontend Developer
- Purpose: route, navigation과 접근 제어 구현 규칙을 정의합니다.
- Audience: Frontend Developer
- Dependencies: `folder-structure.md`, `../../documents/architecture/authentication-flow.md`
- Next Reading: `state-management.md`

## Router

{{ROUTER_AND_VERSION}}

## Route

| Path | Page | 접근 조건 | 관련 요구사항 |
| --- | --- | --- | --- |
| `{{PATH}}` | `{{PAGE}}` | {{ACCESS_RULE}} | `REQ-{{NUMBER}}` |

## 규칙

- route path와 parameter는 한 곳에서 관리합니다.
- page component는 route-level layout와 feature 조합을 담당합니다.
- 인증 및 권한 의미는 공유 문서를 따르고 client guard만으로 보안을 보장하지 않습니다.
- 잘못된 path, loading과 navigation failure 상태를 정의합니다.
