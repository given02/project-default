# project-default

## 목적

`project-default`는 신규 프로젝트를 일관된 방식으로 기획, 구현하고 검증하기 위한 개인 프로젝트 템플릿입니다.

모든 프로젝트에서 유지할 코드 원칙과 기술별 구현 규칙을 Standards로 제공하고, 프로젝트별 작업은 요구사항 하나를 정의부터 테스트 완료까지 반복해 완성합니다. Agent는 저장소 문서를 source of truth로 사용하며 이전 대화에 의존하지 않습니다.

## 핵심 원칙

- 문서는 프로젝트 의미와 결정의 source of truth입니다.
- 코드는 문서화된 요구사항을 구현한 결과입니다.
- 하나의 요구사항 파일이 명세, 진행 상태, 구현 결과와 테스트 증거를 함께 소유합니다.
- 요구사항은 독립적으로 구현하고 검증할 수 있는 사용자 결과 단위로 작성합니다.
- Agent는 문서에 없는 제품 의미나 비즈니스 규칙을 코드에서 추측하지 않습니다.
- 중요한 변경은 관련 문서, 코드와 테스트를 같은 작업에서 정렬합니다.

## 저장소 구조

```text
standards/    프로젝트 운영, 코드와 기술별 구현에 적용할 개인 표준
customs/      요구사항별 명세, 구현과 검증 기록
exceptions/   Standards를 벗어나는 프로젝트별 예외
```

### [Standards](standards/README.md)

기술과 독립적인 공통 원칙과 Spring Boot, Spring Data JPA, React, TypeScript, PostgreSQL의 구체적인 구현 방식을 정의합니다.

개별 프로젝트에서는 `standards/`를 수정하지 않습니다. 변경은 `project-default`의 새 버전 배포를 통해서만 이루어집니다.

### [Workflow](standards/workflow/README.md)

프로젝트를 시작할 때의 질문과 외부 산출물을 생성·갱신하는 반복 절차를 정의합니다.

- 프로젝트 초기 질문: [Start Prompt](standards/workflow/start.md)
- SharePoint와 Figma 원본 접근 절차: [External Document Access](standards/workflow/document-access.md)
- Microsoft Excel과 Figma 산출물 규격: [Artifact Templates](standards/workflow/artifacts.md)

Workflow는 제품 의미를 소유하지 않으며 실제 프로젝트 값과 링크는 Customs에 기록합니다.

### [Customs](customs/README.md)

프로젝트별 요구사항을 하나씩 관리합니다. 각 요구사항 파일에는 다음 내용을 순서대로 작성합니다.

```text
요구사항
→ 기능 명세
→ 화면 설계
→ Database 설계
→ 테스트 계획
→ 코드 작성
→ 테스트 결과
→ 완료
```

화면이나 Database 변경이 없는 요구사항은 해당 구역에 적용하지 않는 이유를 기록하고 넘어갑니다. 구현이 끝난 뒤에도 요구사항 파일은 현재 기능의 명세와 검증 증거로 유지합니다.

### [Exceptions](exceptions/README.md)

특정 요구사항이나 구현에서 Standard를 따를 수 없을 때 적용 범위, 이유, 대안, 대체 규칙, 위험과 검증 방법을 기록합니다.

Exception은 원본 Standard를 수정하지 않으며 파일에 선언된 범위에서만 우선합니다.

## 적용 순서

```text
Standards
→ 현재 Requirement
→ 적용되는 Exceptions
→ 코드와 테스트
```

Agent가 구현 중 누락, 모호함 또는 충돌을 발견하면 코드에서 의미를 추측하지 않습니다. 현재 Requirement를 먼저 갱신하거나 필요한 Exception을 승인한 뒤 구현을 재개합니다.

Agent 역할, 변경 권한, 상태 전이와 역할별 사용법은 [AGENTS.md](AGENTS.md)를 따릅니다. 요구사항 파일 형식과 완료 기준은 [Customs](customs/README.md)를 따릅니다.

## 신규 프로젝트 사용 방법

1. `project-default`의 `main` branch를 새 프로젝트 이름으로 clone합니다.
2. clone 시점의 `.PROJECT_DEFAULT_VERSION`을 프로젝트 기준선으로 사용합니다.
3. `origin`을 신규 프로젝트의 원격 저장소로 변경합니다.
4. [Standards](standards/README.md)는 수정하지 않습니다.
5. Agent에게 `start`를 입력합니다.
6. Codex에서 SharePoint 앱을 Microsoft 계정에 연결하고 화면 설계가 필요하면 Figma 앱도 연결합니다.
7. [Start Prompt](standards/workflow/start.md)의 질문에 프로젝트 설명, 요구사항·기능·DB·테스트 Microsoft Excel 편집 링크와 Figma 링크를 각각 답변합니다.
8. Agent가 [External Document Access](standards/workflow/document-access.md)에 따라 SharePoint와 Figma 원본 접근 및 권한을 확인합니다.
9. Architect가 `customs/PROJECT.md`와 `customs/REQ-001-<영문 이름>.md`를 만들고 요구사항부터 테스트 계획까지 사용자와 순서대로 확정합니다.
10. [Artifact Templates](standards/workflow/artifacts.md)를 기준으로 요구사항 정의서, 기능 명세서, Figma 화면 설계, DB 테이블 정의서와 테스트 시나리오 문서를 함께 갱신합니다.
11. Requirement가 Ready가 되면 Agent가 코드와 테스트를 작성합니다.
12. 실행한 테스트와 실제 결과를 Requirement와 테스트 결과서에 기록하고 Review와 Done으로 전환합니다.
13. 다음 요구사항을 새 파일로 만들고 같은 과정을 반복합니다.

프로젝트 전체 양식을 먼저 작성하지 않습니다. 현재 요구사항을 구현하고 검증하는 데 필요한 내용만 대화를 통해 구체화합니다.

Microsoft Excel과 Figma는 검토와 공유를 위한 산출물입니다. 구현 기준은 저장소의 Requirement이며, 두 내용이 다르면 Requirement를 기준으로 원인을 확인하고 같은 작업에서 동기화합니다.

신규 프로젝트는 clone한 버전을 유지하며 이후 `project-default` 버전으로 자동 또는 수동 업그레이드하지 않습니다.

## 버전과 배포

`project-default` 전체는 Semantic Versioning을 사용합니다.

```text
MAJOR.MINOR.PATCH
```

- MAJOR: 기존 구조나 규칙과 호환되지 않는 변경
- MINOR: 호환 가능한 Standard 또는 템플릿 추가
- PATCH: 의미를 바꾸지 않는 설명, 오탈자와 링크 수정

`main` branch는 항상 신규 프로젝트에서 사용할 수 있는 최신 안정 상태를 유지합니다. 정식 버전은 Git tag와 GitHub Release로 배포합니다.

- 저장소 내부에 이전 버전 문서의 archive 디렉터리를 만들지 않습니다.
- Git tag와 GitHub Release를 공식 버전 아카이브로 사용합니다.
- 버전별 변경 내역은 해당 GitHub Release에 작성합니다.
- 신규 프로젝트는 clone한 시점의 버전을 영구 기준선으로 유지합니다.
