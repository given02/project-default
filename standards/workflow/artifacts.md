# Artifact Templates

## 목적

이 문서는 새 프로젝트에서 요구사항, 기능, 화면, Database와 테스트 산출물을 처음부터 만들 수 있도록 파일 구조와 필수 항목을 정의합니다. 별도의 외부 원본이나 예시 프로젝트를 참조하지 않습니다.

산출물은 프로젝트별 새 Microsoft Excel 통합 문서와 Figma Design 파일로 생성합니다. Excel 통합 문서는 OneDrive 또는 SharePoint에 저장하고 현재 작업 환경에서 접근 가능한 편집 링크를 사용합니다. 원본 문서 접근과 갱신은 [External Document Access](document-access.md)를 따릅니다. 저장소 Requirement가 구현 source of truth이고 외부 산출물은 검토와 공유를 위해 같은 내용을 구조화한 결과입니다.

## 공통 작성 규칙

- 파일 제목은 `[프로젝트명] 산출물명` 형식을 사용합니다.
- 첫 행은 column header로 사용하고 고정, 굵은 글씨, 배경색과 filter를 적용합니다.
- 본문은 줄바꿈을 허용하고 위쪽 정렬을 사용합니다.
- ID column은 문자열로 저장하고 완료된 ID를 다른 의미로 재사용하지 않습니다.
- data 영역에는 병합 cell을 사용하지 않습니다.
- 예시 값 대신 현재 프로젝트의 실제 결정만 기록합니다.
- 변경 내용은 Requirement와 외부 산출물에 같은 작업에서 반영합니다.

모든 Microsoft Excel 산출물은 첫 worksheet에 `Overview`를 둡니다. 상단에는 다음 문서 정보를 기록합니다.

| 항목 | 내용 |
| ---- | ---- |
| 문서명 | `[프로젝트명] 산출물명` |
| 프로젝트 | 프로젝트 이름 |
| 작성자 | 작성 주체 |
| 작성일 | 최초 작성일 |
| 최종 수정일 | 마지막 갱신일 |

하단에는 다음 변경 이력 표를 둡니다.

| 버전 | 변경 내용 | 일자 | 비고 |
| ---- | --------- | ---- | ---- |

## 요구사항 정의서

기능 명세서와 분리된 Microsoft Excel 통합 문서로 생성합니다.

```text
Overview
요구사항 정의서
```

| Requirement ID | 구분 | 요구사항명 | 사용자와 문제 | 요구사항 내용 | 포함 범위 | 제외 범위 | Acceptance Criteria | 우선순위 | 상태 | 비고 |
| -------------- | ---- | ---------- | ------------- | ----------- | --------- | --------- | ------------------- | -------- | ---- | ---- |

- `구분`: 공통, 사용자, 관리자 또는 도메인 영역
- `요구사항 내용`: 사용자가 얻어야 하는 결과와 세부 조건
- `Acceptance Criteria`: Given, When, Then 또는 동등하게 검증 가능한 조건
- `상태`: Draft, Ready, In Progress, Blocked, Review, Done 또는 Cancelled
- 하나의 행은 하나의 Requirement ID를 소유합니다.

## 기능 명세서

요구사항 정의서와 분리된 Microsoft Excel 통합 문서로 생성합니다.

```text
Overview
기능 명세서
```

| Function ID | Requirement ID | Depth 1 | Depth 2 | Depth 3 | 기능명 | 기능 설명 | 입력과 Validation | 처리와 Business Rule | 출력과 상태 변화 | 권한 | 오류 처리 | 개발 공수(MD) | 개발 레벨 | 개발 계획 | 비고 |
| ----------- | -------------- | ------- | ------- | ------- | ------ | --------- | ----------------- | -------------------- | ---------------- | ---- | --------- | ------------- | --------- | --------- | ---- |

- Depth는 사용자 영역, 메뉴와 세부 기능의 계층을 표현합니다.
- 하나의 Requirement가 여러 기능으로 나뉘면 Function ID를 각각 부여합니다.
- API와 외부 연동이 있으면 입력, 처리, 출력과 오류 column에 계약을 함께 기록합니다.
- 개발 공수, 레벨과 계획은 사용자가 요청하거나 근거가 있을 때만 작성합니다.

## 화면 설계서

화면 설계는 프로젝트별 Figma Design 파일에서 관리합니다. 다음 page 구조를 기본으로 사용합니다.

```text
00_Cover        프로젝트와 문서 정보
01_Foundations  color, typography, spacing, grid와 breakpoint
02_Components   공통 component와 variant
10_User         사용자 화면과 상태
20_Admin        관리자 화면과 상태, 적용하지 않으면 생략
90_Prototype    주요 사용자 flow와 interaction 연결
```

화면 frame에는 Requirement ID와 화면 이름을 함께 표시합니다. 각 화면은 다음 내용을 표현합니다.

- route 또는 표시 위치와 접근 조건
- 주요 component, data와 사용자 action
- initial, loading, empty, error, disabled, success와 unauthorized 상태
- desktop, tablet과 mobile 반응형 동작
- keyboard, focus, accessible name과 오류 연결
- 주요 interaction과 화면 전환

Requirement에는 Figma file URL과 관련 page 또는 node URL을 기록합니다. 화면이 없는 프로젝트는 `해당 없음`과 이유를 기록합니다.

## DB 테이블 정의서

하나의 Microsoft Excel 통합 문서에 다음 구조로 worksheet를 만듭니다.

```text
00_Overview      문서 정보와 변경 이력
01_Table_List    전체 table 목록
NN_<table_name>  table별 정책과 column 정의
99_Indexes       unique와 index 통합 목록
```

### 00_Overview

문서명, 프로젝트, Database 종류와 version, 기본 schema, 작성자, 작성일과 최종 수정일을 기록합니다. 하단에는 버전, 변경 내용, 일자와 비고로 구성된 변경 이력 표를 둡니다.

### 01_Table_List

| No | 테이블명 | 테이블 설명 | 소유 도메인 | 관련 Requirement | 상태 | 비고 |
| --- | -------- | ----------- | ----------- | ---------------- | ---- | ---- |

### NN_&lt;table_name&gt;

상단에는 다음 table 정보를 기록합니다.

| 항목 | 내용 |
| ---- | ---- |
| Table Name | 실제 table 이름 |
| Description | table의 제품 의미 |
| Related Requirement | 관련 Requirement ID |
| Create Policy | 생성 조건과 주체 |
| Read Policy | 조회 조건과 권한 |
| Update Policy | 수정 조건과 정합성 규칙 |
| Delete Policy | hard delete, soft delete, archive 또는 삭제 불가 정책 |
| Retention Policy | 보존과 복구 정책 |

하단에는 다음 column 정의 표를 둡니다.

| 컬럼명 | 데이터 타입 | PK | FK | Nullable | Default | Unique | Index | 설명 | 비고 |
| ------ | ----------- | --- | --- | -------- | ------- | ------ | ----- | ---- | ---- |

### 99_Indexes

| 구분 | 이름 | 테이블 | 컬럼 또는 조건 | 관련 Requirement | 설명 |
| ---- | ---- | ------ | --------------- | ---------------- | ---- |

- `구분`은 UNIQUE 또는 INDEX를 사용합니다.
- 여러 column으로 구성되면 순서를 포함해 쉼표로 구분합니다.
- partial index라면 조건을 함께 기록합니다.

## 테스트 시나리오 및 결과서

하나의 Microsoft Excel 통합 문서에 다음 세 worksheet를 순서대로 만듭니다.

```text
Overview
테스트 시나리오 목록
테스트 케이스 및 결과
```

### Overview

문서명, 프로젝트, 테스트 대상 version, 환경, 작성자, 작성일과 최종 수정일을 기록합니다. 하단에는 버전, 변경 내용, 일자와 비고로 구성된 변경 이력 표를 둡니다.

### 테스트 시나리오 목록

| Requirement ID | Depth 1 | Depth 2 | Depth 3 | 시나리오 ID | 시나리오 제목 | 테스트 목적 | 우선순위 | 상태 |
| -------------- | ------- | ------- | ------- | ----------- | ------------- | ----------- | -------- | ---- |

- 시나리오 ID는 `TS-영역-3자리 번호` 형식을 사용합니다.
- Requirement의 정상 흐름, 오류, 권한과 경계를 시나리오로 분리합니다.

### 테스트 케이스 및 결과

| Requirement ID | 시나리오 ID | 시나리오 제목 | TC ID | TC 제목 | 사전 조건 | 실행 절차와 입력 | 예상 결과 | 실제 결과 | 결과(P/F) | 증거 | 결함·재검증 | 비고 |
| -------------- | ----------- | ------------- | ----- | ------- | --------- | -------------- | --------- | --------- | --------- | ---- | ----------- | ---- |

- TC ID는 `TC-영역-시나리오번호-케이스번호` 형식을 사용합니다.
- 테스트 계획 단계에는 사전 조건, 실행 절차, 입력과 예상 결과까지 작성합니다.
- 구현 후 실제 결과, P/F, log·screenshot·report 등의 증거와 결함·재검증 내용을 작성합니다.
- 실행하지 못한 테스트는 비워두지 않고 이유와 영향을 기록합니다.

## Requirement 단계별 반영 위치

| Requirement 단계 | 산출물 | 반영 위치 |
| ---------------- | ------ | --------- |
| 요구사항 정의 | 요구사항 정의 Microsoft Excel | `요구사항 정의서` |
| 기능 명세 | 기능 명세 Microsoft Excel | `기능 명세서` |
| 화면 설계 | Figma Design | 관련 page와 node |
| Database 설계 | DB 테이블 정의 Microsoft Excel | `01_Table_List`, table별 worksheet와 `99_Indexes` |
| 테스트 계획 | 테스트 Microsoft Excel | 시나리오와 케이스 worksheet의 계획 column |
| 테스트 결과 | 테스트 Microsoft Excel | 케이스 worksheet의 실제 결과, P/F, 증거와 재검증 column |

외부 산출물에 현재 Requirement를 표현할 항목이 부족하면 의미를 생략하지 않고 필요한 column이나 상세 영역을 추가합니다. 저장소와 외부 산출물이 충돌하면 Requirement를 기준으로 원인을 확인하고 같은 작업에서 정렬합니다.
