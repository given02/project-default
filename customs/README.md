# Customs

## 목적

`customs/`는 프로젝트의 요구사항을 독립적인 사용자 결과 단위로 관리합니다.

요구사항마다 파일 하나를 만들고 요구사항 정의, 기능 명세, 화면 설계, Database 설계, 테스트 계획, 구현 결과와 테스트 결과를 같은 파일에 순서대로 기록합니다. 별도의 Task 문서는 만들지 않습니다.

`start` 초기화가 완료되면 `PROJECT.md`에 프로젝트 설명과 Google Sheets·Figma 산출물 링크를 기록합니다. Requirement는 구현의 source of truth이고 외부 문서는 검토와 공유를 위한 동기화 산출물입니다.

외부 산출물을 생성하고 작성할 때는 [Artifact Templates](../ARTIFACTS.md)에 자체적으로 정의된 구조를 따릅니다.

## 프로젝트 정보 파일

`PROJECT.md`는 Requirement나 Task가 아니라 프로젝트 설명과 공통 산출물 링크를 보관하는 파일입니다. 다음 형식을 사용합니다.

```markdown
# Project

## 프로젝트 설명

사용자가 설명한 프로젝트 목적, 사용자, 문제와 첫 번째 완성 목표

## 외부 산출물

| 산출물 | 형식과 위치 | 링크 | 적용 여부 |
| ------ | ----------- | ---- | --------- |
| 요구사항 정의서 | Google Sheets `요구사항 정의서` 시트 | 편집 링크 | 적용 |
| 기능 명세서 | 같은 Google Sheets `기능 명세서` 시트 | 편집 링크 | 적용 |
| 화면 설계서 | Figma Design | 편집 링크 또는 해당 없음 | 적용 / 해당 없음 |
| DB 테이블 정의서 | Google Sheets | 편집 링크 또는 해당 없음 | 적용 / 해당 없음 |
| 테스트 시나리오 및 결과서 | Google Sheets | 편집 링크 | 적용 |
```

- 요구사항 정의서, 기능 명세서와 테스트 시나리오 및 결과서는 필수입니다.
- 화면이나 Database가 없는 프로젝트는 해당 산출물을 `해당 없음`으로 기록합니다.
- 링크가 바뀌면 `PROJECT.md`를 즉시 갱신합니다.
- credential, access token과 비공개 공유 암호를 링크 옆에 기록하지 않습니다.

## 파일 이름과 Requirement ID

```text
REQ-<3자리 번호>-<영문 이름>.md
```

예:

```text
REQ-001-user-login.md
REQ-002-profile-update.md
REQ-003-account-deletion.md
```

- 번호는 `001`부터 순차 증가합니다.
- 영문 이름은 lowercase kebab-case를 사용합니다.
- 파일 번호와 문서의 Requirement ID를 일치시킵니다.
- 하나의 ID는 하나의 사용자 결과만 소유합니다.
- 삭제하거나 대체한 ID를 다른 의미로 재사용하지 않습니다.
- 다른 Requirement와 Exception은 파일 경로 대신 Requirement ID를 참조합니다.

## Requirement 크기

하나의 Requirement는 사용자가 확인할 수 있는 결과 하나를 구현하고 독립적으로 검증할 수 있어야 합니다.

- 여러 결과가 서로 독립적으로 배포되거나 되돌릴 수 있으면 Requirement를 분리합니다.
- Backend와 Frontend가 함께 필요한 하나의 사용자 결과는 같은 Requirement에서 관리할 수 있습니다.
- 선행 작업이 필요하면 선행 Requirement ID를 기록합니다.
- 프로젝트 전체 설계나 미래 기능을 한 파일에 미리 작성하지 않습니다.

## 작성 순서

```text
요구사항 정의
→ 기능 명세
→ 화면 설계
→ Database 설계
→ 테스트 계획
→ Ready 승인
→ 코드와 테스트 작성
→ 테스트 결과 기록
→ Review
→ Done
```

화면이나 Database 변경이 없으면 해당 구역에 `적용하지 않음`과 이유를 기록합니다. 테스트 계획까지 완료하기 전에는 코드를 작성하지 않습니다.

## 파일 형식

각 Requirement 파일은 다음 형식을 사용합니다.

```markdown
# REQ-001: 요구사항 이름

## 상태

Draft

## 담당 역할

Architect, Backend Developer, Frontend Developer 중 필요한 역할

## 목표

사용자가 얻게 될 독립적으로 확인 가능한 결과

## 선행 Requirement

- `REQ-번호` 또는 해당 없음

## 적용 Exception

- `EXC-번호` 또는 해당 없음

## 산출물 반영 위치

- 요구사항 정의서: `요구사항 정의서` 시트의 row 또는 range
- 기능 명세서: `기능 명세서` 시트의 row 또는 range
- 화면 설계서: Figma page와 node URL / 해당 없음
- DB 테이블 정의서: sheet와 table 범위 / 해당 없음
- 테스트 시나리오 및 결과서: sheet와 test ID 범위

## 1. 요구사항 정의

### 사용자와 문제

- 사용자:
- 해결할 문제:

### 범위

- 포함:
- 제외:

### Acceptance Criteria

- Given ..., when ..., then ...

### 용어와 제약

- 새로 정의하거나 기존 Requirement에서 참조할 용어
- 기술, 보안, 운영 또는 일정 제약

## 2. 기능 명세

### 정상 흐름

1. 사용자 행동
2. 시스템 동작
3. 완료 결과

### Business Rule

- 조건, 결과와 예외

### 입력과 출력

- 입력, validation과 오류
- 출력과 상태 변화

### 계약

- API, 인증, 권한과 외부 연동
- 적용하지 않으면 이유

## 3. 화면 설계

- 화면 또는 route
- 구성 요소와 사용자 action
- loading, empty, error, disabled, success와 권한 상태
- 반응형과 접근성
- 화면이 없으면 적용하지 않는 이유

## 4. Database 설계

- 새로 만들거나 변경할 table과 column
- type, nullable, default, PK, FK, unique와 check constraint
- index와 주요 query
- 생성, 수정, 삭제, 보존과 migration
- Database 변경이 없으면 적용하지 않는 이유

## 5. 테스트 계획

| ID | 검증 대상 | 사전 조건 | 실행 또는 입력 | 기대 결과 |
| --- | --------- | --------- | ------------ | --------- |

- 실행할 formatter, lint, test와 build 명령
- 필요한 수동, 통합 또는 end-to-end 검증

## 6. 구현 결과

### Backend

- 구현 요약:
- 변경 파일:
- migration 또는 생성 파일:

### Frontend

- 구현 요약:
- 변경 파일:

## 7. 테스트 결과

| 테스트 ID | 실제 결과 | 상태 | 증거 또는 비고 |
| --------- | --------- | ---- | -------------- |

- 실행한 명령:
- 실행하지 못한 검증과 이유:
- 발견한 문제와 수정 내용:

## Blocked

- 사유:
- 필요한 결정 또는 선행 작업:
- 영향 범위와 이미 수행한 작업:

## 검토 결과

- 명세와 구현 일치 여부:
- 남은 작업:
- 승인자:
- 승인일:
```

필요하지 않은 구현 역할과 항목에는 `해당 없음`과 이유를 기록합니다.

테스트 ID는 `<Requirement ID>-T<2자리 번호>` 형식을 사용합니다. 예: `REQ-001-T01`. 같은 Requirement 안에서 완료된 테스트 ID를 다른 의미로 재사용하지 않습니다.

## 상태와 변경 권한

상태 정의와 전이는 [AGENTS.md](../AGENTS.md#requirement-상태)를 따릅니다.

- Architect는 Requirement를 생성하고 명세, 테스트 계획과 검토 결과를 작성합니다.
- Developer는 명세를 읽기 전용으로 사용하고 상태, Blocked, 자신이 담당한 구현 결과와 테스트 결과만 작성합니다.
- 명세 변경이 필요하면 Developer가 임의로 수정하지 않고 Blocked 사유와 필요한 결정을 기록합니다.

## 외부 산출물 동기화

각 Requirement 단계에서 다음 산출물을 기본으로 갱신합니다.

| Requirement 단계 | 외부 산출물 | 반영 내용 |
| ---------------- | ---------------- | --------- |
| 요구사항 정의 | 요구사항 정의서 | 사용자, 문제, 범위와 acceptance criteria |
| 기능 명세 | 기능 명세서 | 정상 흐름, Business Rule, 입력·출력과 계약 |
| 화면 설계 | 화면 설계서 | 화면, route, 구성 요소, action, 상태, 반응형과 접근성 |
| Database 설계 | DB 테이블 정의서 | table, column, type, key, constraint, index와 migration 영향 |
| 테스트 계획 | 테스트 시나리오 및 결과서 | test ID, 사전 조건, 입력·절차와 기대 결과 |
| 테스트 결과 | 테스트 시나리오 및 결과서 | 실제 결과, 성공 여부, 증거, 결함과 재검증 결과 |

- 저장소 Requirement를 먼저 갱신하고 같은 작업에서 Google Sheets 또는 Figma 산출물을 동기화합니다.
- Requirement의 `산출물 반영 위치`에 실제 sheet, range, Figma page·node 또는 test ID를 기록합니다.
- 두 내용이 충돌하면 Requirement를 기준으로 원인을 확인하고 외부 산출물을 정렬합니다.
- 문서 접근 도구나 권한이 없으면 반영하지 못한 이유와 반영할 정확한 내용을 Requirement에 기록하고 사용자에게 전달합니다.
- 외부 문서 갱신 여부를 확인하지 못했으면 완료했다고 기록하지 않습니다.

## Ready 기준

- 목표가 독립적으로 확인 가능한 사용자 결과입니다.
- 요구사항 범위와 acceptance criteria가 구체적이고 검증 가능합니다.
- 정상 흐름, Business Rule, 입력, 출력과 오류가 결정되어 있습니다.
- 필요한 API, 인증, 권한과 외부 계약이 결정되어 있습니다.
- 화면과 Database 설계가 작성되었거나 적용하지 않는 이유가 있습니다.
- 테스트 항목, 기대 결과와 실행할 검증 방법이 구현 전에 작성되어 있습니다.
- 선행 Requirement가 Done 상태입니다.
- 적용되는 Exception이 Requirement에 연결되어 있습니다.
- Google Sheets와 Figma 산출물에 관련 명세와 테스트 계획이 반영되었거나, 접근할 수 없는 이유와 반영할 내용이 기록되어 있습니다.
- 구현 범위에 placeholder, 모호함 또는 문서 충돌이 없습니다.

## Review와 Done 기준

Review로 전환하기 전에 다음을 확인합니다.

- 코드와 테스트가 Requirement 범위와 acceptance criteria를 충족합니다.
- 필요한 migration과 생성 파일이 함께 작성되었습니다.
- 계획한 테스트의 실제 결과와 증거가 기록되었습니다.
- Google Sheets 테스트 시나리오 및 결과서에 실제 결과가 반영되었거나, 접근할 수 없는 이유와 반영할 내용이 기록되었습니다.
- 실행하지 못한 검증과 이유가 기록되었습니다.
- 발견한 누락과 충돌이 해결되었거나 Blocked로 전환되었습니다.
- 구현 요약과 변경 파일이 기록되었습니다.

Done으로 전환하기 전에 Architect는 명세, 코드와 테스트 결과의 일치를 검토하고 남은 작업이 없음을 기록합니다.

## 변경과 보존

- 진행 중 요구사항이 바뀌면 코드보다 명세와 테스트 계획을 먼저 갱신합니다.
- 완료된 기능의 현재 의미가 바뀌면 새 Requirement를 만들고 기존 Requirement ID를 선행 또는 관련 항목으로 참조합니다.
- Done 또는 Cancelled Requirement 파일을 삭제하지 않습니다.
- 현재 상태와 구현·검증 증거를 파일에 유지하고 상세 변경 이력은 Git history에서 확인합니다.
- 별도의 Requirement index나 Task 목록을 관리하지 않습니다.
