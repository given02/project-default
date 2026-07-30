# Frontend Project Environment

- Owner: Frontend Developer
- Purpose: Frontend 기술 버전, dependency와 환경 규칙을 정의합니다.
- Audience: Frontend Developer
- Dependencies: `../{{DEPENDENCY_MANIFEST}}`
- Next Reading: `folder-structure.md`

## 기술

| 항목 | 선택 | 버전 | Source Of Truth |
| --- | --- | --- | --- |
| Runtime | {{RUNTIME}} | {{VERSION}} | {{VERSION_FILE}} |
| Language | {{LANGUAGE}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |
| Framework | {{FRAMEWORK}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |
| Build Tool | {{BUILD_TOOL}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |
| Test | {{TEST_TOOLS}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |
| Styling | {{STYLING_SOLUTION}} | {{VERSION}} | {{DEPENDENCY_MANIFEST}} |

## 환경 변수

| 이름 | 필수 | 공개 가능 | 설명 |
| --- | --- | --- | --- |
| `{{ENV_NAME}}` | 예 | {{YES_OR_NO}} | {{DESCRIPTION}} |

## 규칙

- 브라우저 번들에 포함되는 환경 변수에는 secret을 넣지 않습니다.
- dependency와 version은 실제 manifest를 source of truth로 사용합니다.
- 지원 브라우저와 runtime 정책을 명시합니다.
