# Project Environment

## Repository 구조

| 항목                          | 결정                                                  |
| ----------------------------- | ----------------------------------------------------- |
| Repository 구성               | Monorepo                                              |
| 프로젝트 root                 | `.`                                                   |
| Backend root                  | `backend/`                                            |
| Frontend root                 | `frontend/`                                           |
| 공유 도구와 설정 위치         | Repository root                                       |
| 생성 파일과 build output 정책 | source만 commit하고 dependency 및 build output은 제외 |

## Backend 프로젝트 식별자

Backend를 사용하지 않으면 적용하지 않는 이유와 재검토 조건을 기록합니다.

| 항목                   | 결정                  |
| ---------------------- | --------------------- |
| Application name       | 작성 필요             |
| Group                  | 작성 필요             |
| Artifact               | 작성 필요             |
| Base package           | 작성 필요             |
| Packaging              | Jar                   |
| Build DSL              | Kotlin DSL            |
| Main source directory  | `src/main/java/`      |
| Test source directory  | `src/test/java/`      |
| Resource directory     | `src/main/resources/` |
| Build output directory | `build/`              |

## Frontend 프로젝트 식별자

Frontend를 사용하지 않으면 적용하지 않는 이유와 재검토 조건을 기록합니다.

| 항목                       | 결정                                |
| -------------------------- | ----------------------------------- |
| Application name           | 작성 필요                           |
| Package name               | 작성 필요                           |
| Package manager            | npm                                 |
| Package manager version    | 선택한 Node.js LTS에 포함된 version |
| Workspace 사용 여부와 위치 | 사용하지 않음                       |
| Source directory           | `src/`                              |
| Public asset directory     | `public/`                           |
| Import alias               | `@` → `src/`                        |
| Build output directory     | `dist/`                             |

## 공통 개발 환경

| 항목                   | 결정                                         | Source Of Truth           |
| ---------------------- | -------------------------------------------- | ------------------------- |
| 지원 OS                | 작성 필요                                    | 이 문서                   |
| Container 사용         | 로컬 dependency에 Docker Compose 사용        | compose 설정              |
| 로컬 dependency 실행   | Docker Compose                               | compose 설정              |
| 기본 timezone과 locale | UTC 저장, 사용자 표시는 프로젝트 요구에 따름 | 설정과 API 계약           |
| package registry       | Maven Central, npm registry                  | build manifest와 lockfile |

## Backend 환경

Backend를 사용하지 않으면 적용하지 않는 이유와 재검토 조건을 기록합니다.
기술과 목표 version은 [Technology Stack](050-technology-stack.md)을 단일 Source Of Truth로 사용합니다.

| 항목       | 선택                             | 목표 version          | 실제 Source Of Truth       |
| ---------- | -------------------------------- | --------------------- | -------------------------- |
| Language   | Technology Stack의 Backend 선택  | Technology Stack 참조 | version 또는 manifest 파일 |
| Framework  | Technology Stack의 Backend 선택  | Technology Stack 참조 | dependency manifest        |
| Build tool | Technology Stack의 Backend 선택  | Technology Stack 참조 | wrapper 또는 설정          |
| Database   | Technology Stack의 Database 선택 | Technology Stack 참조 | 로컬 환경과 배포 설정      |
| Migration  | Technology Stack의 Backend 선택  | Technology Stack 참조 | dependency manifest        |
| Test       | Technology Stack의 Backend 선택  | Technology Stack 참조 | dependency manifest        |
| API 문서화 | Technology Stack의 Backend 선택  | Technology Stack 참조 | dependency manifest        |

### Backend 생성 방식

| 항목                                | 결정                                                                                                                                        |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| 생성 도구 또는 방식                 | Spring Initializr                                                                                                                           |
| 생성 명령 또는 입력값               | 이 문서의 프로젝트 식별자와 Technology Stack의 version을 사용하고 Gradle·Kotlin·Jar를 선택                                                  |
| 초기 dependency                     | Spring Web, Validation, Spring Data JPA, PostgreSQL Driver, Flyway, Actuator, Spring REST Docs, Spring Boot Test, Testcontainers PostgreSQL |
| 초기 build plugin                   | Spring Boot, dependency management, Spotless, Checkstyle                                                                                    |
| 생성 후 제거하거나 변경할 기본 파일 | 생성된 `HELP.md` 제거                                                                                                                       |

### Backend 명령

| 목적                  | 명령                                             |
| --------------------- | ------------------------------------------------ |
| 설치 또는 초기화      | 별도 설치 없음. Repository의 Gradle Wrapper 사용 |
| 실행                  | `./gradlew bootRun`                              |
| Format                | `./gradlew spotlessApply`                        |
| Static analysis       | `./gradlew check`                                |
| Test                  | `./gradlew test`                                 |
| Build                 | `./gradlew build`                                |
| Migration 상태와 적용 | 작성 필요                                        |

## Frontend 환경

Frontend를 사용하지 않으면 적용하지 않는 이유와 재검토 조건을 기록합니다.
기술과 목표 version은 [Technology Stack](050-technology-stack.md)을 단일 Source Of Truth로 사용합니다.

| 항목       | 선택                             | 목표 version          | 실제 Source Of Truth            |
| ---------- | -------------------------------- | --------------------- | ------------------------------- |
| Runtime    | Technology Stack의 Frontend 선택 | Technology Stack 참조 | version 파일                    |
| Language   | Technology Stack의 Frontend 선택 | Technology Stack 참조 | dependency manifest             |
| Framework  | Technology Stack의 Frontend 선택 | Technology Stack 참조 | dependency manifest             |
| Build tool | Technology Stack의 Frontend 선택 | Technology Stack 참조 | dependency manifest             |
| Styling    | Technology Stack의 Frontend 선택 | Technology Stack 참조 | dependency manifest 또는 source |
| Test       | Technology Stack의 Frontend 선택 | Technology Stack 참조 | dependency manifest             |

### Frontend 생성 방식

| 항목                                | 결정                                                                     |
| ----------------------------------- | ------------------------------------------------------------------------ |
| 생성 도구 또는 방식                 | Vite React TypeScript template                                           |
| 생성 명령 또는 입력값               | `npm create vite@latest`에서 React와 TypeScript 선택                     |
| 초기 dependency                     | React, TypeScript, Vite, Vitest, React Testing Library, ESLint, Prettier |
| 생성 후 제거하거나 변경할 기본 파일 | 예제 logo, counter, style을 제거하고 빈 application shell로 교체         |

### Frontend 명령

| 목적              | 명령                                |
| ----------------- | ----------------------------------- |
| 설치              | `npm install`                       |
| 개발 실행         | `npm run dev`                       |
| Format            | `npm run format`                    |
| Lint와 type check | `npm run lint`, `npm run typecheck` |
| Test              | `npm run test`                      |
| Build             | `npm run build`                     |

## Service와 Port

| Service   | Local host·port | Test      | Production 접근 | Health check |
| --------- | --------------- | --------- | --------------- | ------------ |
| 작성 필요 | 작성 필요       | 작성 필요 | 작성 필요       | 작성 필요    |

## 환경 변수

실제 secret 값은 기록하지 않습니다.

| 이름        | 사용 영역                 | 필수        | 공개 가능   | 안전한 예시 | 설명      |
| ----------- | ------------------------- | ----------- | ----------- | ----------- | --------- |
| `작성_필요` | Backend / Frontend / Tool | 예 / 아니요 | 예 / 아니요 | 작성 필요   | 작성 필요 |

## 설정과 Secret

| 항목                         | 결정                                                                           |
| ---------------------------- | ------------------------------------------------------------------------------ |
| 설정 파일 전략               | Backend는 version 관리되는 `application.yml`, Frontend는 Vite 환경 파일을 사용 |
| 환경별 설정 주입             | 환경 변수로 기본 설정을 덮어씀                                                 |
| Secret 저장과 주입           | Git에 commit하지 않고 환경 변수 또는 배포 환경의 secret store로 주입           |
| Client 공개 환경 변수 prefix | `VITE_`                                                                        |
| 로컬 예시 파일               | secret 없이 필요한 key만 담은 `.env.example`을 commit                          |

## 지원 환경

| 구분     | 지원 범위                    | 검증 방법 |
| -------- | ---------------------------- | --------- |
| Browser  | 적용하지 않음 또는 작성 필요 | 작성 필요 |
| Runtime  | 작성 필요                    | 작성 필요 |
| Database | 적용하지 않음 또는 작성 필요 | 작성 필요 |

## 완료 기준

- Repository 구성과 Backend·Frontend 실제 root 경로가 확정되어 있습니다.
- Backend의 application name, group, artifact, base package, packaging과 build DSL이 확정되어 있습니다.
- Frontend의 package name, package manager, source directory, import alias와 build output이 확정되어 있습니다.
- 프로젝트 생성 방식, 입력값과 초기 dependency가 확정되어 있습니다.
- 새 Agent가 문서의 명령만으로 프로젝트를 설치, 실행, 검증하고 build할 수 있습니다.
- 실제 version은 manifest와 wrapper에서 확인할 수 있습니다.
- 필요한 환경 변수에는 설명과 안전한 예시가 있습니다.
- secret과 client 공개 값이 명확히 구분됩니다.
