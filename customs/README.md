# Customs

## 목적

`customs/`는 현재 프로젝트의 기획, 디자인, 기술 선택과 구현 명세를 관리합니다.

프로젝트마다 달라지는 사용자, 기능, 화면, 도메인, 데이터베이스, API, 환경과 검증 기준을 기록합니다. 실제 프로젝트를 구현하는 데 필요한 모든 프로젝트 고유 정보는 이 디렉터리에서 찾을 수 있어야 합니다.

작성 책임과 변경 권한은 [AGENTS.md](../AGENTS.md)의 Architect 규칙을 따릅니다. 사용자는 최소한의 Project Brief를 제공하고, Architect는 대화를 통해 현재 목표에 필요한 명세를 문서에 반영합니다. 관련 명세가 구현 가능한 상태가 되면 [Tasks](../tasks/README.md)의 기준으로 작업을 분할합니다.

## 파일 이름

- 파일 이름은 `<3자리 순서>-<영문 이름>.md` 형식을 사용합니다.
- 순서 번호는 `010`부터 시작해 `010`씩 증가합니다.
- 번호는 최초 작성 순서를 나타냅니다.
- 이미 사용한 번호는 다른 의미로 재사용하지 않습니다.
- 중간 문서가 필요하면 비어 있는 번호를 사용합니다.
- `README.md`만 순서 번호를 사용하지 않습니다.

## 문서 목록

```text
customs/
├── README.md
├── 010-project-overview.md
├── 020-glossary.md
├── 030-product-requirements.md
├── 040-business-rules.md
├── 050-technology-stack.md
├── 060-product-roadmap.md
├── 100-information-architecture.md
├── 110-user-flows.md
├── 120-screen-specifications.md
├── 130-design-system.md
├── 200-domain-model.md
├── 210-system-architecture.md
├── 220-authentication-and-authorization.md
├── 230-data-lifecycle.md
├── 240-database-schema.md
├── 250-api-contract.md
├── 300-project-environment.md
├── 310-test-strategy.md
└── 320-release-and-operations.md
```

## 프로젝트 기획

| 파일                          | 관리하는 내용                                       |
| ----------------------------- | --------------------------------------------------- |
| `010-project-overview.md`     | 프로젝트 목적, 문제, 사용자, 목표, 성공 지표와 범위 |
| `020-glossary.md`             | 사용자, 문서, 코드와 API에서 사용할 표준 용어       |
| `030-product-requirements.md` | 기능, 사용자 가치, 우선순위와 acceptance criteria   |
| `040-business-rules.md`       | 제품 규칙, invariant, 조건, 결과와 예외             |
| `050-technology-stack.md`     | 사용할 기술, 적용할 기술 Standard, 도구와 목표 버전 |
| `060-product-roadmap.md`      | milestone, 기능 우선순위, 선행 관계와 보류 항목     |

## UX와 UI 디자인

| 파일                              | 관리하는 내용                                        |
| --------------------------------- | ---------------------------------------------------- |
| `100-information-architecture.md` | navigation, page, route와 정보 계층                  |
| `110-user-flows.md`               | 사용자 행동, 시스템 반응과 성공·실패 분기            |
| `120-screen-specifications.md`    | 화면 목적, 데이터, action, validation과 UI 상태      |
| `130-design-system.md`            | 색상, typography, spacing, token과 component variant |

## 도메인과 시스템 설계

| 파일                                      | 관리하는 내용                                      |
| ----------------------------------------- | -------------------------------------------------- |
| `200-domain-model.md`                     | Aggregate, Entity, Value Object, 관계와 invariant  |
| `210-system-architecture.md`              | component, 책임, 데이터 소유권, 의존성과 외부 연동 |
| `220-authentication-and-authorization.md` | 인증, session 또는 token, 역할과 권한              |
| `230-data-lifecycle.md`                   | 생성, 수정, 삭제, 보존, 복구와 개인정보 처리       |
| `240-database-schema.md`                  | 실제 table, column, key, constraint와 index        |
| `250-api-contract.md`                     | 실제 endpoint, 요청, 응답, validation, 권한과 오류 |

## 개발과 운영

| 파일                            | 관리하는 내용                                        |
| ------------------------------- | ---------------------------------------------------- |
| `300-project-environment.md`    | 프로젝트 디렉터리, 도구, 명령, 환경 변수와 실행 환경 |
| `310-test-strategy.md`          | test 수준, 검증 범위, 필수 명령과 완료 기준          |
| `320-release-and-operations.md` | 배포, migration, rollback, 관측과 복구 기준          |

## 추적 ID

문서 사이에서 같은 개념을 안정적으로 참조하기 위해 다음 ID를 사용합니다.

```text
REQ-001   Product Requirement
BR-001    Business Rule
FLOW-001  User Flow
SCR-001   Screen
API-001   API Operation
```

- ID는 종류별로 `001`부터 순차 증가합니다.
- 하나의 ID는 하나의 의미만 소유합니다.
- 삭제하거나 대체한 ID를 다른 의미로 재사용하지 않습니다.
- 이름이나 위치가 바뀌어도 의미가 같으면 기존 ID를 유지합니다.
- 다른 문서는 내용을 복사하지 않고 소유 문서의 ID를 참조합니다.

## 작성 규칙

- `project-default`에 아직 프로젝트 값이 없는 항목은 `작성 필요`로 표시합니다.
- 신규 프로젝트는 [Project Overview](010-project-overview.md)의 최소 Project Brief부터 작성합니다.
- Architect가 사용자와 대화하며 현재 목표에 필요한 문서와 항목만 질문하고 실제 결정으로 교체합니다.
- 파일 번호는 여러 문서를 함께 작성할 때 의존성을 확인하기 위한 권장 순서이며 전체 문서의 선행 완료를 의미하지 않습니다.
- 이미 작성된 기본값은 프로젝트 요구와 충돌하지 않으면 유지하며, 변경할 때는 해당 문서에 이유와 영향을 기록합니다.
- 아직 검토하지 않았고 현재 목표와 관련 없는 문서에는 template의 `작성 필요`가 남아 있어도 됩니다.
- 현재 Task의 구현 범위와 연결된 문서에는 해결되지 않은 `작성 필요`가 남아 있으면 안 됩니다.
- 현재 목표에서 사용하지 않기로 결정한 항목은 `적용하지 않음`, 이유와 재검토 조건을 기록합니다.
- 각 개념은 하나의 Customs 문서에서만 정의합니다.
- 프로젝트별 실제 값과 선택을 명확하게 작성합니다.
- 요구사항에는 검증 가능한 acceptance criteria를 작성합니다.
- 비즈니스 규칙은 조건, 결과, 예외와 검증 예시를 포함합니다.
- UI는 loading, empty, error, disabled, success와 권한 상태를 정의합니다.
- API는 요청, 응답, validation, 인증, 권한과 오류를 정의합니다.
- Database는 실제 table, column, key, constraint와 index를 정의합니다.
- 중요한 선택에는 이유, 검토한 대안과 영향을 기록합니다.
- 적용할 기술 Standard는 경로나 규칙 ID로 참조하고 내용을 복사하지 않습니다.
- 관련 내용이 변경되면 영향을 받는 Customs 문서를 같은 작업에서 정렬합니다.

## 적용하지 않는 문서

현재 프로젝트에 적용되지 않는 문서는 삭제하지 않습니다.

모든 문서의 적용 여부를 프로젝트 시작 시점에 미리 판단할 필요는 없습니다. 문서가 현재 목표와 관련될 때 적용 여부를 판단합니다.

문서에 다음 내용을 기록합니다.

- 적용하지 않음
- 적용하지 않는 이유
- 향후 재검토 조건

이를 통해 아직 검토하지 않은 문서와 의도적으로 적용하지 않는 문서를 구분합니다.

## 점진적 작성 순서

1. [Project Overview](010-project-overview.md)에 최소 Project Brief를 작성합니다.
2. [Technology Stack](050-technology-stack.md)의 기본값을 적용하고 변경할 항목만 기록합니다.
3. 첫 번째로 완성할 사용자 결과를 기준으로 관련 Requirement와 Business Rule을 정의합니다.
4. 해당 기능에 필요한 UX, 도메인, 아키텍처, 인증, 데이터, Database와 API 문서만 구체화합니다.
5. 환경, 테스트, 릴리스와 운영 문서는 관련 Task를 시작하기 전에 필요한 범위만 작성합니다.
6. 관련 문서가 아래 Task Ready 기준을 충족하면 Task를 생성하고 구현을 시작합니다.

Glossary와 Roadmap도 필요가 생길 때 확장합니다. 대화에서 확정된 지속성 있는 결정은 구현 전에 반드시 소유 문서에 반영합니다.

## Task Ready 기준

- Task가 참조하는 Customs 항목과 관련 계약이 작성되어 있습니다.
- 해당 범위에서 사용한 용어가 [Glossary](020-glossary.md)와 일치하거나 Glossary에 추가되어 있습니다.
- 관련 요구사항, 비즈니스 규칙, 화면, 도메인, Database와 API 사이에 충돌이 없습니다.
- 구현 범위에 해결되지 않은 placeholder가 없습니다.
- acceptance criteria와 공유 계약을 검증할 방법이 정의되어 있습니다.
- 실제 기술과 version이 필요한 Task라면 manifest, wrapper와 설정 파일에 기록할 값이 결정되어 있습니다.

다른 기능이나 아직 검토하지 않은 Customs의 placeholder는 현재 Task의 Ready 전환을 막지 않습니다.

## 읽기 순서

프로젝트를 처음 시작할 때는 이 README, [Project Overview](010-project-overview.md), [Technology Stack](050-technology-stack.md)을 먼저 읽습니다. 이후 현재 목표와 연결된 문서만 읽고 작성합니다.

여러 관련 문서를 처음 정의할 때는 파일 번호를 의존성 확인을 위한 권장 순서로 사용합니다.

기능을 변경할 때는 해당 기능의 Requirement ID에서 시작해 연결된 Business Rule, Flow, Screen, Domain, Database와 API 항목을 함께 확인합니다.
