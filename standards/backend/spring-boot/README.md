# Spring Boot Standards

## 목적

`standards/backend/spring-boot/`는 Requirement에서 Spring Boot를 Backend framework로 선택한 프로젝트에 적용할 고정 구현 규칙을 정의합니다.

## 문서

| 문서                                            | 내용                                        |
| ----------------------------------------------- | ------------------------------------------- |
| `BE-SPR-01-application-convention.md`           | 구성, dependency injection과 환경 설정      |
| `BE-SPR-02-async-and-observability-convention.md` | 비동기 실행과 관측                           |
| `BE-SPR-03-web-convention.md`                   | Controller, DTO, validation과 오류 응답     |
| `BE-SPR-04-http-convention.md`                  | 직렬화, HTTP와 security context             |
| `BE-SPR-05-testing-convention.md`               | Controller API 문서와 경계 통합 테스트       |
| `BE-SPR-06-flyway-convention.md`                | 관계형 Database의 Flyway migration          |
| `BE-SPR-07-lombok-convention.md`                | Lombok 적용 범위와 domain·JPA 안전성        |
| `BE-SPR-08-java-format-convention.md`           | Java 형식, 줄바꿈과 자동 formatter          |
| `BE-SPR-09-test-source-layout.md`               | 단위·API·통합 테스트 위치와 실행            |
| `BE-SPR-10-dependency-naming-convention.md`     | 생성자 주입 field와 매개변수의 타입 기반 명명 |
| `spring-data-jpa/`                              | Spring Data JPA를 선택한 persistence 규칙   |
