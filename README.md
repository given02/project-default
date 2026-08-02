# project-default

## 목적

`project-default`는 신규 프로젝트를 일관된 방식으로 기획, 설계, 구현하고 검증하기 위한 개인 프로젝트 템플릿입니다.

모든 프로젝트에서 유지할 개발 원칙과 기술별 구현 규칙을 기준선으로 제공하고, 프로젝트마다 달라지는 제품 요구사항과 설계 내용을 순서대로 작성할 수 있게 합니다. Agent는 저장소 문서를 source of truth로 사용하며, 이전 대화에 의존하지 않고 문서와 작업 지시를 기반으로 코드를 작성합니다.

## 핵심 원칙

- 문서는 프로젝트 의미와 결정의 source of truth입니다.
- 코드는 문서화된 요구사항과 계약을 구현한 결과입니다.
- 모든 개념은 하나의 소유자와 하나의 source of truth를 가집니다.
- 모든 프로젝트에 적용되는 규칙과 프로젝트마다 달라지는 내용을 분리합니다.
- Agent는 문서에 없는 제품 의미나 비즈니스 규칙을 코드에서 추측하지 않습니다.
- 중요한 변경은 관련 문서, 코드와 테스트를 같은 작업에서 정렬합니다.

## 문서 구조

```text
standards/    공통 원칙과 기술별 구현 방식을 포함하는 개인 개발 표준
customs/      프로젝트 기획, 설계와 구현을 위한 프로젝트별 실행 명세
exceptions/   Standards를 벗어나 현재 적용하는 프로젝트별 예외
tasks/        Customs를 구현 가능한 범위로 나눈 Agent 작업 지시
```

### [Standards](standards/README.md)

기술과 독립적인 공통 원칙과 Spring Boot, Spring Data JPA, React, TypeScript, PostgreSQL의 구체적인 구현 방식을 함께 정의합니다.

개별 프로젝트에서는 `standards/`를 수정하지 않습니다. 변경은 `project-default`의 새 버전 배포를 통해서만 이루어집니다.

### [Customs](customs/README.md)

Agent가 실제 제품 코드를 작성할 수 있도록 프로젝트별 내용을 정의합니다.

- 프로젝트 목적, 사용자와 해결할 문제
- 기술 스택과 환경
- 요구사항과 비즈니스 규칙
- 사용자 여정, UI 흐름과 화면 명세
- 디자인 시스템
- 도메인 모델과 시스템 아키텍처
- 데이터베이스 schema
- 인증, API 요청·응답과 오류 계약
- 테스트, 릴리스와 운영 기준

Customs는 적용할 기술 Standard를 선택하지만 Standard 자체를 재정의할 수 없습니다. 충돌이 필요하면 Exception을 작성합니다.

### [Exceptions](exceptions/README.md)

특정 프로젝트나 기능에서 Standard 규칙을 따를 수 없을 때 적용 범위, 이유, 대안, 대체 규칙, 위험과 검증 방법을 기록합니다.

Exception은 원본 규칙을 수정하지 않으며 파일에 선언된 범위에서만 우선합니다.

### [Tasks](tasks/README.md)

Customs의 요구사항과 설계를 구현 가능한 작업 단위로 분할합니다.

Task는 새로운 제품 의미를 정의하지 않고 관련 Standards, Customs와 Exceptions를 참조합니다. Agent는 Task의 범위, 완료 기준과 검증 방법에 따라 코드와 테스트를 작성합니다.

## 적용 순서

```text
Standards
→ Customs에서 선택한 기술 Standards
→ 관련 Customs
→ 적용되는 Exceptions
→ 현재 Task
→ 코드와 테스트
```

Agent가 구현 중 누락, 모호함 또는 충돌을 발견하면 코드에서 의미를 추측하지 않습니다. 관련 Customs를 먼저 갱신하거나 필요한 Exception을 승인한 뒤 Task를 재개합니다.

Agent 역할, 변경 권한과 역할별 사용법은 [AGENTS.md](AGENTS.md)를 따릅니다. Task 파일 형식과 상태 전이는 [Tasks](tasks/README.md)를 따릅니다.

## 신규 프로젝트 사용 방법

1. `project-default`의 `main` branch를 새 프로젝트 이름으로 clone합니다.
2. clone 시점의 `.PROJECT_DEFAULT_VERSION`을 프로젝트 기준선으로 사용합니다.
3. `origin`을 신규 프로젝트의 원격 저장소로 변경합니다.
4. [Standards](standards/README.md)는 수정하지 않습니다.
5. [Customs](customs/README.md)를 번호순으로 작성해 프로젝트 요구사항과 설계를 확정합니다.
6. [Tasks](tasks/README.md)의 기준에 따라 구현할 기능을 Task로 분할합니다.
7. Agent가 관련 문서를 읽고 코드와 테스트를 작성합니다.

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
