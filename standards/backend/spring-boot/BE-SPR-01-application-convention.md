# Spring Boot Application Convention

## 구성과 주입

- **STD-BE-SPR-010** application 진입점은 최상위 base package에 두고 component scan 범위를 명시적으로 유지합니다.
- **STD-BE-SPR-011** production component의 dependency는 생성자 주입을 사용합니다.
- **STD-BE-SPR-012** field injection과 application context에서 bean을 직접 조회하는 service locator 방식을 사용하지 않습니다.
- **STD-BE-SPR-013** 구현이 하나뿐인 내부 의존성에도 테스트만을 위한 불필요한 interface를 만들지 않으며 외부 경계와 교체가 필요한 경계에는 port를 둡니다.
- **STD-BE-SPR-014** bean의 순환 의존성을 허용하지 않고 책임과 의존성 방향을 다시 나눕니다.

## 설정

- **STD-BE-SPR-015** 관련 설정 값은 검증 가능한 `@ConfigurationProperties` 타입으로 묶고 코드 곳곳에서 문자열 key로 직접 읽지 않습니다.
- **STD-BE-SPR-016** secret과 환경별 값은 외부에서 주입하고 repository의 설정 파일에 실제 값을 저장하지 않습니다.
- **STD-BE-SPR-017** profile은 환경별 infrastructure 연결과 설정 차이에 사용하고 비즈니스 동작을 profile 조건으로 분기하지 않습니다.
- **STD-BE-SPR-018** application 시작에 필수인 설정은 누락되거나 유효하지 않을 때 즉시 실패하게 검증합니다.
- **STD-BE-SPR-019** dependency와 plugin 버전의 source of truth는 build manifest와 wrapper로 유지합니다.
