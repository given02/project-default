# Backend Standards

## 목적

`standards/backend/`는 Backend 기술에 공통으로 적용되는 아키텍처, 코드, persistence와 파일 저장 규칙을 정의합니다.

## 문서

| 문서                                 | 내용                                      |
| ------------------------------------ | ----------------------------------------- |
| `BE-01-architecture-convention.md`   | 계층 책임과 의존성                        |
| `BE-02-model-boundary-convention.md` | 모델 변환과 orchestration 경계            |
| `BE-03-code-convention.md`           | 명명, 오류와 로그                         |
| `BE-04-testing-convention.md`        | Service 단위 TDD와 필요한 통합 테스트     |
| `BE-05-persistence-convention.md`    | 저장 모델과 조회                          |
| `BE-06-transaction-convention.md`    | transaction과 동시성                      |
| `BE-07-file-storage-convention.md`   | 파일 검증, 저장, 접근과 생명주기          |
| `spring-boot/`                       | Spring Boot를 선택한 프로젝트의 구현 규칙 |

Backend 작업은 이 디렉터리의 공통 규칙을 먼저 적용하고, Requirement에서 Spring Boot를 선택한 경우 `spring-boot/` 규칙을 함께 적용합니다.
