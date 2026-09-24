# Spring Boot Test Source Layout

## 위치와 실행

- **STD-BE-SPR-090** Java 기반 Spring Boot의 단위, Web/API와 persistence·외부 경계 통합 테스트는 모두 module의 `src/test/java`에 두고, 테스트 resource는 `src/test/resources`에 둡니다. 별도 `src/integrationTest` source set을 만들지 않습니다.
- **STD-BE-SPR-091** 테스트 package는 검증 대상의 production package를 따라가며, 통합 테스트에는 `*IntegrationTest`처럼 목적을 알 수 있는 이름을 사용합니다. 테스트 유형을 구분하기 위해 최상위 source directory를 늘리지 않습니다.
- **STD-BE-SPR-092** 통합 테스트를 별도로 실행해야 하면 같은 `src/test` source set 안에서 tag 또는 test filter로 구분합니다. 표준 `check` 또는 동등한 검증 명령은 Requirement에 필요한 단위·Web/API·통합 테스트를 빠짐없이 실행합니다.
- **STD-BE-SPR-093** 실제 경계 검증이 필요한 Requirement에서만 통합 테스트와 환경을 추가합니다. 새 프로젝트를 시작할 때 빈 통합 테스트 directory나 전용 task를 미리 만들지 않습니다.
