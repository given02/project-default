# Frontend API Client Convention

## 계약과 구성

- **STD-FE-010** API 함수는 feature 또는 resource 소유권에 따라 구성하고 화면 component 안에 transport 세부사항을 직접 구현하지 않습니다.
- **STD-FE-011** 요청, 응답, enum, nullable과 오류 type은 Requirement의 기능 명세와 계약에 일치시킵니다.
- **STD-FE-012** HTTP 성공과 제품 동작의 성공을 API 계약에 따라 구분합니다.
- **STD-FE-013** base URL, timeout과 공통 header는 하나의 client 구성 경계에서 관리합니다.
- **STD-FE-014** retry는 멱등성과 오류 종류를 확인하고 mutation을 무조건 자동 재시도하지 않습니다.

## 인증과 오류

- **STD-FE-015** 인증 정보의 저장과 전송은 Requirement의 인증 계약을 따르며 client가 독자적인 인증 방식을 만들지 않습니다.
- **STD-FE-016** client route guard와 UI 숨김을 서버 권한 검증의 대체 수단으로 사용하지 않습니다.
- **STD-FE-017** 사용자 메시지와 개발 진단 정보를 분리하고 내부 stack, token과 민감한 응답을 화면이나 client 로그에 노출하지 않습니다.
- **STD-FE-018** 인증 만료와 권한 부족을 구분하고 계약에 정의된 재인증 또는 접근 거부 흐름을 적용합니다.
