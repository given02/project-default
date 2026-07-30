# State Management

- Owner: Frontend Developer
- Purpose: Frontend 상태의 종류별 소유권과 도구를 정의합니다.
- Audience: Frontend Developer
- Dependencies: `frontend-convention.md`, `api-client.md`
- Next Reading: `api-client.md`

## 상태 분류

| 상태 | 소유 위치 | 도구 | 예 |
| --- | --- | --- | --- |
| Local UI | interaction을 소유하는 component | {{LOCAL_STATE_TOOL}} | 열림, 선택, 입력 |
| URL | router | {{ROUTER}} | 필터, 페이지, 공유 가능한 선택 |
| Server | server-state layer | {{SERVER_STATE_TOOL}} | API 조회 결과 |
| Cross-feature client | 최소 범위의 store/provider | {{GLOBAL_STATE_TOOL_OR_NONE}} | {{EXAMPLE}} |
| Persisted client | 명시적인 storage adapter | {{PERSISTENCE_TOOL_OR_NONE}} | 사용자 환경설정 |

## 규칙

- 같은 값을 여러 state layer에 중복 저장하지 않습니다.
- server data를 일반 global store에 복제하지 않습니다.
- 권한과 business invariant를 Frontend state로 재정의하지 않습니다.
- persisted state에는 version과 migration 또는 안전한 초기화 정책을 둡니다.
