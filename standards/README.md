# Standards

## 목적

`standards/`는 모든 프로젝트에서 일관되게 유지할 개인 개발 표준의 source of truth입니다.

기술과 독립적인 공통 원칙과 Spring Boot, Spring Data JPA, React, TypeScript, PostgreSQL의 구체적인 구현 방식을 함께 정의합니다.

## 불변성

clone으로 생성한 실제 프로젝트에서는 어떤 역할도 `standards/`를 수정할 수 없습니다.

Standard 자체의 변경은 `project-default`에서 Template Maintainer가 수행하고 새로운 버전으로만 배포합니다. 실제 프로젝트에서 Standard를 준수할 수 없으면 루트 문서에 정의된 예외 절차를 따릅니다.

`project-default`에서도 사용자가 템플릿 표준 변경을 명시적으로 요청한 작업에서만 `standards/`를 변경합니다.

## 적용 범위

```text
standards/
├── workflow/                    프로젝트 시작과 산출물 운영 절차
├── common/                      기술 독립적인 아키텍처, 코드 품질, 테스트와 보안
├── backend/
│   ├── 공통 Backend 규칙
│   └── spring-boot/
│       └── spring-data-jpa/
├── frontend/
│   ├── 공통 Frontend 규칙
│   └── react/
└── database/
    ├── 공통 Database 규칙
    └── postgresql/
```

기술별 규칙도 모든 프로젝트에 배포되는 고정 Standard입니다. 실제 프로젝트에는 사용 중인 기술 경로의 Standard만 적용합니다.

`workflow/`는 모든 프로젝트에 배포되는 운영 Standard입니다. 프로젝트별 값을 포함하지 않고 시작 질문, 산출물 생성과 동기화 절차를 정의합니다.

## 표준의 효력

Standard에 정의된 규칙은 적용 범위 안에서 모두 의무입니다.

- 실제 프로젝트에서 Standard를 변경하거나 선택적으로 무시할 수 없습니다.
- Standard를 준수할 수 없으면 구현 전에 Exception이 필요합니다.
- Exception에는 대상 규칙 ID, 범위, 이유, 위험, 대체 규칙과 검증 방법을 기록합니다.
- 특정 조건에서만 적용되는 규칙은 강도를 낮추지 않고 적용 조건을 명시합니다.
- 프로젝트가 자유롭게 선택할 수 있는 내용은 Standard에 포함하지 않습니다.
- 특정 기술을 선택했을 때 적용할 구현 방식은 해당 기술의 Standard 하위 디렉터리에서 정의합니다.
- 설명, 배경과 예시는 규칙으로 해석하지 않습니다.

## 규칙 ID

Exception과 관련 문서가 특정 규칙을 안정적으로 참조할 수 있도록 규범적인 Standard에는 고유 ID를 부여합니다.

```text
STD-COMMON-010    Common
STD-BE-010        Backend
STD-BE-SPR-010    Spring Boot
STD-BE-JPA-010    Spring Data JPA
STD-FE-010        Frontend
STD-FE-REACT-010  React
STD-FE-TS-010     TypeScript
STD-DB-010        Database
STD-DB-PG-010     PostgreSQL
```

### ID 규칙

- 파일 번호 `NN`은 규칙 ID `NN0`부터 `NN9`까지의 범위를 소유합니다.
- 각 파일의 첫 규칙은 `NN0`부터 시작하고 같은 파일 안에서 순차 증가합니다.
- 한 파일에 규칙이 10개를 초과하면 다음 번호 파일로 책임을 분리합니다.
- 하나의 ID는 하나의 검증 가능한 규칙만 소유합니다.
- 문서 위치나 제목이 바뀌어도 같은 의미의 규칙은 기존 ID를 유지합니다.
- 삭제하거나 대체한 ID를 다른 의미로 재사용하지 않습니다.
- 규칙을 분리하면 기존 ID는 핵심 의미에 유지하고 새로운 규칙에 새 ID를 부여합니다.
- 규칙 의미가 변경되면 `project-default` 버전 영향과 기존 Exception 영향을 검토합니다.

## 파일 이름

규칙 ID를 소유하는 구현 Standard 파일은 다음 형식을 사용합니다.

```text
<RULE-PREFIX>-<2자리 구간>-<lowercase-kebab-case>.md
```

예:

```text
COMMON-04-testing-principles.md
BE-JPA-05-transaction-convention.md
DB-PG-03-index-convention.md
```

- 파일 prefix는 파일 안의 규칙 ID prefix와 일치해야 합니다.
- 두 자리 파일 번호는 같은 디렉터리와 prefix 안에서 `01`부터 빈 번호 없이 순차 증가합니다.
- 파일 번호 `01`, `02`, `03`은 각각 규칙 ID `010~019`, `020~029`, `030~039`와 대응합니다.
- 같은 디렉터리에서 동일한 prefix와 파일 번호를 재사용하지 않습니다.
- 파일의 책임이 10개 규칙 범위를 넘으면 다음 번호 파일로 분리합니다.

## Standard 작성 규칙

Template Maintainer는 Standard를 작성하거나 변경할 때 다음을 준수합니다.

- 프로젝트 이름, 도메인, 실제 endpoint, route, table과 환경 값을 포함하지 않습니다.
- 프로젝트가 채워야 하는 중괄호 형식의 placeholder를 포함하지 않습니다.
- 규칙의 목적, 적용 범위와 검증 가능한 행동을 명확히 작성합니다.
- 하나의 개념을 하나의 문서에서만 정의하고 다른 문서는 규칙 ID와 링크로 참조합니다.
- 공통 원칙은 기술별 디렉터리에 복사하지 않고 기술별 문서에서 구체적인 구현 방식만 정의합니다.
- framework, ORM과 database vendor의 API는 해당 기술 디렉터리에서만 정의합니다.
- 예외가 불가능한 이상론보다 실제 프로젝트에서 반복 적용할 수 있는 기준을 정의합니다.
- Standard 변경과 관련된 문서 링크, 규칙 참조와 Agent 읽기 순서를 함께 검토합니다.
- `.PROJECT_DEFAULT_VERSION`이 변경되면 MAJOR, MINOR와 PATCH 구분 없이 같은 작업에서 `updates/<대상 버전>.md` self-contained 마이그레이션 프롬프트와 `updates/README.md` index를 작성합니다.
- 대응하는 update 문서가 없거나 기존 프로젝트에서 변경을 재현할 수 없으면 새 버전 변경을 완료하거나 배포하지 않습니다.

## 읽기 순서

1. `README.md`
2. 프로젝트를 시작하거나 산출물을 갱신할 때 `workflow/`
3. `common/`
4. 현재 역할의 `backend/` 또는 `frontend/`
5. 프로젝트에서 사용하는 Backend 또는 Frontend 기술 Standard
6. 데이터 저장을 사용하는 경우 `database/`
7. 프로젝트에서 사용하는 Database 기술 Standard

작업과 관계없는 모든 Standard를 매번 읽을 필요는 없지만 현재 역할과 선택된 기술에 적용되는 규칙은 작업 전에 확인합니다.
