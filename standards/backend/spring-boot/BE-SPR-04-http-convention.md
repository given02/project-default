# Spring Boot HTTP Convention

## 직렬화와 HTTP

- **STD-BE-SPR-040** 전역 ObjectMapper 설정 변경은 모든 API에 미치는 영향을 검토하고 endpoint별 임시 설정으로 계약을 분기하지 않습니다.
- **STD-BE-SPR-041** 시간과 enum은 암묵적인 framework 기본값에 의존하지 않고 API 계약의 표현을 명시합니다.
- **STD-BE-SPR-042** 생성, 변경과 삭제 endpoint는 재시도 및 중복 요청 영향을 검토하고 필요한 경우 idempotency 계약을 적용합니다.
- **STD-BE-SPR-043** 인증과 인가는 client 입력이 아니라 검증된 SecurityContext와 서버 정책을 기준으로 수행합니다.
