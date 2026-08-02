# Backend Testing Convention

## 기준

- **STD-BE-040** 비즈니스 규칙은 단위 테스트로, persistence와 외부 연동은 실제 경계를 사용하는 통합 테스트로 검증합니다.
- **STD-BE-041** API 테스트는 성공, validation, 인증, 권한, not-found와 계약에 정의된 주요 오류를 검증합니다.
