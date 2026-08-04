# Spring Boot Testing Convention

## 기준

- **STD-BE-SPR-050** framework가 필요 없는 domain과 application 규칙 테스트에는 Spring context를 시작하지 않습니다.
- **STD-BE-SPR-051** MVC mapping, serialization, validation과 security filter 검증에는 목적에 맞는 web slice 테스트를 사용합니다.
- **STD-BE-SPR-052** 전체 context 테스트는 bean wiring, configuration과 여러 실제 경계의 통합을 검증할 때만 사용합니다.
- **STD-BE-SPR-053** 테스트에서 production bean을 광범위하게 mock으로 교체해 실제 wiring 오류를 숨기지 않습니다.
- **STD-BE-SPR-054** configuration property, profile과 조건부 bean의 중요한 조합은 application 시작 테스트로 검증합니다.
- **STD-BE-SPR-055** API 테스트는 Requirement 계약의 status, header, body, validation, 인증과 권한을 검증합니다.
- **STD-BE-SPR-056** 외부 시스템 통합 테스트는 명시적 adapter 경계에서 수행하고 실패, timeout과 잘못된 응답을 포함합니다.
