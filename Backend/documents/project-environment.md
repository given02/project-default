# Backend Project Environment

- Owner: Backend Developer
- Purpose: Backend 기술 버전, dependency와 환경 규칙을 정의합니다.
- Audience: Backend Developer
- Dependencies: `../{{DEPENDENCY_MANIFEST}}`
- Next Reading: `architecture-convention.md`

## 기술

| 항목 | 선택 | 버전 | Source Of Truth |
| --- | --- | --- | --- |
| Language | {{LANGUAGE}} | {{VERSION}} | {{VERSION_FILE_OR_MANIFEST}} |
| Framework | {{FRAMEWORK}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |
| Build Tool | {{BUILD_TOOL}} | {{VERSION}} | {{WRAPPER_OR_CONFIG}} |
| Database | {{DATABASE_OR_NONE}} | {{VERSION}} | {{LOCAL_ENV_CONFIG}} |
| Migration | {{MIGRATION_TOOL_OR_NONE}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |
| Test | {{TEST_TOOLS}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |
| API Docs | {{API_DOC_TOOL_OR_NONE}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |

## 환경

- 기본 개발 환경: {{DEFAULT_ENVIRONMENT}}
- 설정 파일 전략: {{CONFIG_FILE_STRATEGY}}
- 로컬 dependency 실행: {{LOCAL_DEPENDENCY_STRATEGY}}
- secret 주입: {{SECRET_INJECTION_STRATEGY}}

## 규칙

- dependency와 plugin 버전은 실제 manifest를 source of truth로 사용합니다.
- secret과 개인 credential을 저장소에 commit하지 않습니다.
- 필요한 환경 변수는 안전한 예시값과 함께 루트 환경 문서에 기록합니다.
- 기술 또는 버전이 바뀌면 같은 작업에서 이 문서를 갱신합니다.
