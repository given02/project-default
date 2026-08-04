# Technology Stack

## 선택 원칙

- 이 문서는 사용할 기술과 적용할 Standard 경로를 선택합니다.
- 표에 작성된 기본값은 별도 프로젝트 요구나 변경 기록이 없으면 자동으로 적용합니다.
- 사용자는 기본값을 그대로 사용할 때 이 문서를 별도로 채울 필요가 없습니다.
- 기본값을 변경하면 선택 이유와 검토한 대안을 이 문서에 기록합니다.
- dependency의 정확한 설치 version은 manifest와 wrapper가 source of truth이며 목표 version은 이 문서에 기록합니다.
- `최신 안정`과 `최신 LTS`는 프로젝트 Bootstrap 시점에 공식 지원 범위 안에서 확정하고 manifest 또는 wrapper에 고정합니다.
- Standard에 없는 기술을 선택하면 구현 규칙을 추측하지 않고 필요한 Standard 추가 또는 프로젝트 범위의 명시적 설계를 먼저 검토합니다.

## Backend

| 항목         | 선택                                        | 목표 version                                 | 적용 Standard                                                                                                                                                | 선택 이유 |
| ------------ | ------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------- |
| Language     | Java                                        | Spring Boot가 지원하는 최신 LTS              | [Backend Standards](../standards/backend/README.md)                                                                                                          | 기본값    |
| Framework    | Spring Boot                                 | 최신 안정                                    | [Spring Boot Standards](../standards/backend/spring-boot/README.md)                                                                                          | 기본값    |
| Persistence  | Spring Data JPA                             | Spring Boot dependency management            | [Spring Data JPA Standards](../standards/backend/spring-boot/spring-data-jpa/README.md)                                                                      | 기본값    |
| Build tool   | Gradle Wrapper                              | 선택한 Java·Spring Boot와 호환되는 최신 안정 | 관련 wrapper와 build manifest                                                                                                                                | 기본값    |
| Code quality | Spotless + Checkstyle                       | Gradle·Java와 호환되는 최신 안정             | [Code Quality](../standards/common/COMMON-03-code-quality.md)                                                                                                | 기본값    |
| Migration    | Flyway                                      | Spring Boot와 호환되는 최신 안정             | [Database Standards](../standards/database/README.md)                                                                                                        | 기본값    |
| Test         | JUnit 5 + Spring Boot Test + Testcontainers | Spring Boot와 호환되는 최신 안정             | [Backend Testing](../standards/backend/BE-04-testing-convention.md), [Spring Boot Testing](../standards/backend/spring-boot/BE-SPR-05-testing-convention.md) | 기본값    |
| API 문서화   | Spring REST Docs                            | Spring Boot와 호환되는 최신 안정             | 관련 build manifest                                                                                                                                          | 기본값    |

## Frontend

| 항목         | 선택                           | 목표 version                          | 적용 Standard                                                                  | 선택 이유 |
| ------------ | ------------------------------ | ------------------------------------- | ------------------------------------------------------------------------------ | --------- |
| Runtime      | Node.js                        | 최신 LTS                              | 관련 version 파일                                                              | 기본값    |
| Language     | TypeScript                     | React·Vite와 호환되는 최신 안정       | [Type Safety](../standards/frontend/react/FE-TS-01-type-safety-convention.md)  | 기본값    |
| Framework    | React                          | 최신 안정                             | [React Standards](../standards/frontend/react/README.md)                       | 기본값    |
| Build tool   | Vite                           | React와 호환되는 최신 안정            | 관련 manifest                                                                  | 기본값    |
| Code quality | ESLint + Prettier              | React·TypeScript와 호환되는 최신 안정 | [Code Quality](../standards/common/COMMON-03-code-quality.md)                  | 기본값    |
| Styling      | CSS Modules                    | React·Vite에 포함된 기능              | [UI Convention](../standards/frontend/FE-03-ui-convention.md)                  | 기본값    |
| Test         | Vitest + React Testing Library | Vite·React와 호환되는 최신 안정       | [React Testing](../standards/frontend/react/FE-REACT-06-testing-convention.md) | 기본값    |

## Database와 외부 서비스

| 항목           | 선택          | 목표 version                   | 적용 Standard                                                         | 용도           |
| -------------- | ------------- | ------------------------------ | --------------------------------------------------------------------- | -------------- |
| Database       | PostgreSQL    | 배포 환경이 지원하는 최신 안정 | [PostgreSQL Standards](../standards/database/postgresql/README.md)    | 기본값         |
| Cache          | 적용하지 않음 | 해당 없음                      | 해당 없음                                                             | 필요할 때 선택 |
| Message broker | 적용하지 않음 | 해당 없음                      | 해당 없음                                                             | 필요할 때 선택 |
| File storage   | 적용하지 않음 | 해당 없음                      | [File Storage](../standards/backend/BE-07-file-storage-convention.md) | 필요할 때 선택 |
| 외부 API       | 적용하지 않음 | 해당 없음                      | 해당 없음                                                             | 필요할 때 선택 |

## 프로젝트별 변경

변경이 없으면 이 표를 비워둡니다.

| 결정 항목 | 기본값 대신 사용할 선택 | 변경 이유 | 검토한 대안 | 변경 영향 |
| --------- | ------------------------- | --------- | ----------- | --------- |

## 완료 기준

- 변경 기록이 없는 항목에는 이 문서의 기본값이 결정으로 적용됩니다.
- 기본값을 변경한 기술과 목표 version이 프로젝트별 변경 표에 기록되어 있습니다.
- 각 기술에 적용할 Standard 경로가 연결되어 있습니다.
- 선택 기능은 실제 도입을 검토할 때 적용 여부와 이유를 기록합니다.
- Bootstrap Task가 프로젝트 생성 도구와 dependency를 추측하지 않아도 됩니다.
