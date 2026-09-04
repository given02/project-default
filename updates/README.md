# Updates

## 목적

`updates/`는 기존 프로젝트에 새 `project-default` 기준을 선택적으로 적용하기 위한 버전별 마이그레이션 프롬프트를 제공합니다.

이 디렉터리는 이전 Standard의 사본을 보관하는 archive가 아닙니다. 각 문서는 바로 이전 배포 버전에서 대상 버전으로 이동하는 데 필요한 변경 목적, 실행 권한, 변경 범위와 검증 기준만 소유합니다. 버전별 전체 상태와 이력은 Git tag와 GitHub Release가 소유합니다.

## 사용 방법

1. 대상 프로젝트의 `.PROJECT_DEFAULT_VERSION`을 확인합니다.
2. 현재 버전 다음에 해당하는 update 문서를 선택합니다.
3. 문서의 `복사할 프롬프트` 전체를 대상 프로젝트의 새 Agent 대화에 붙여넣습니다.
4. Agent가 제시한 사전 확인 결과와 변경 범위를 검토합니다.
5. Agent가 변경, 검증과 commit을 완료하면 `.PROJECT_DEFAULT_VERSION`을 확인합니다.
6. 여러 버전이 뒤처졌다면 중간 update를 생략하지 않고 같은 절차를 순서대로 반복합니다.

예:

```text
6.0.0 프로젝트
→ 6.1.0 update 실행
→ 7.0.0 update 실행
→ 7.1.0 update 실행
```

## 파일 이름

대상 버전을 파일 이름으로 사용합니다.

```text
updates/<대상 버전>.md
```

각 문서는 다음 정보를 포함합니다.

- 출발 버전과 대상 버전
- 호환성과 적용 전 조건
- 그대로 복사할 수 있는 self-contained 프롬프트
- 템플릿 관리 파일과 프로젝트 보호 파일
- 완료 조건과 권장 commit 메시지

## 새 버전 작성 규칙

Template Maintainer는 MAJOR, MINOR와 PATCH를 포함해 `.PROJECT_DEFAULT_VERSION`을 새 버전으로 변경할 때마다 같은 변경 작업에서 `updates/<대상 버전>.md`를 반드시 생성합니다.

- 출발 버전은 변경 직전의 최신 배포 버전 하나로 고정합니다.
- 대상 버전은 `.PROJECT_DEFAULT_VERSION`과 파일 이름을 정확히 일치시킵니다.
- 프롬프트는 다른 대화 기록이나 `project-default` 원격 저장소 없이 실행할 수 있는 self-contained 형식으로 작성합니다.
- 변경된 의미, 파일 범위, 보호 영역, 검증 명령과 commit 메시지를 빠짐없이 포함합니다.
- 변경할 내용이 설명이나 오탈자뿐인 PATCH라도 update 문서를 생략하지 않습니다.
- `제공되는 Update` 표에 새 행을 추가합니다.
- update 문서, index, 버전 파일과 실제 변경은 하나의 release 변경 범위로 검증합니다.
- Git tag와 GitHub Release 설명은 update 문서를 대체하지 않습니다.

대응하는 update 문서가 없거나 현재 변경을 재현하는 데 필요한 내용이 부족하면 새 버전은 완료되거나 배포 가능한 상태가 아닙니다.

## 적용 원칙

- 업데이트는 자동으로 실행하지 않습니다.
- 사용자가 공식 update 프롬프트를 붙여넣은 경우에만 해당 버전 변경을 명시적으로 승인한 것으로 봅니다.
- Agent는 update 프롬프트에 선언된 파일과 의미만 변경합니다.
- 현재 버전이 출발 버전과 다르면 변경하지 않고 필요한 중간 update를 안내합니다.
- 프로젝트별 요구사항, 결정, 구현과 비밀정보를 덮어쓰지 않습니다.
- 변경 대상에 겹치는 미커밋 변경이 있으면 중단하고 사용자에게 알립니다.
- 모든 검증이 성공한 뒤 버전 파일을 대상 버전으로 갱신하고 commit합니다.
- 같은 update를 이미 적용한 프로젝트에서는 다시 변경하거나 중복 commit하지 않습니다.

## 관리 영역

update 문서가 변경할 수 있는 기본 템플릿 관리 영역은 다음과 같습니다.

- `.PROJECT_DEFAULT_VERSION`
- `.codex/agents/`
- `AGENTS.md`
- `README.md`의 project-default 운영 구역
- `standards/`
- `customs/README.md`
- `exceptions/README.md`
- `updates/`

다음 프로젝트별 영역은 update 문서가 명시적으로 migration을 요구하지 않는 한 변경하지 않습니다.

- `customs/PROJECT.md`
- `customs/REQ-*.md`
- `exceptions/EXC-*.md`
- production code, test, configuration과 migration
- 프로젝트별 README 내용과 사용자가 추가한 문서

충돌이 있으면 프로젝트 내용을 삭제해 템플릿과 맞추지 않습니다. update 목적을 보존하면서 기존 내용을 병합하거나 판단이 필요하면 사용자에게 에스컬레이션합니다.

## 제공되는 Update

| 출발 버전 | 대상 버전 | 문서 | 주요 변경 |
| --------- | --------- | ---- | --------- |
| `6.0.0` | `6.1.0` | [6.1.0](6.1.0.md) | SharePoint 원본 문서 접근 절차와 선택적 update 체계 |
| `6.1.0` | `7.0.0` | [7.0.0](7.0.0.md) | Service 단위 테스트 TDD, Controller API 문서와 Flyway 필수화 |
| `7.0.0` | `7.1.0` | [7.1.0](7.1.0.md) | 역할별 컨텍스트와 모델 분리, 실행 소유권과 순차 상태 전이 |
