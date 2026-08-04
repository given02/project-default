# Artifact Templates

## 목적

이 문서는 새 프로젝트에서 사용할 외부 산출물의 원본 양식과 작성 규칙을 정의합니다.

원본 파일은 참고용이며 직접 수정하지 않습니다. 새 프로젝트를 시작할 때 Google Drive의 네이티브 파일 복사 기능으로 전체 원본을 한 번 복사한 뒤, 불필요한 예시 데이터와 시트를 사본에서 정리합니다. 다운로드 후 재업로드하는 방식으로 양식을 재구성하지 않습니다.

## 요구사항 정의서와 기능 명세서

- 원본: [시스템 개발 업무범위 및 구축기간](https://docs.google.com/spreadsheets/d/1n4C8ni987O8Tb0pyvQgq9bPmmPzGjAreq8v7eOKwdvI/edit)
- 요구사항 정의서: 두 번째 시트 `요구사항 정의서` (`sheetId: 110155102`)
- 기능 명세서: 세 번째 시트 `기능 명세서` (`sheetId: 0`)

새 프로젝트에서는 원본 통합 문서 전체를 복사한 뒤 다음 두 시트를 기본 산출물로 사용합니다. 개발 일정 시트는 사용자가 일정 관리도 요청한 경우에만 유지합니다.

### 요구사항 정의서 구조

| 구분 | 내용 | 비고 |
| ---- | ---- | ---- |

- `구분`: 공통, 사용자, 관리자 등 요구사항 영역
- `내용`: 검증 가능한 요구사항과 세부 조건
- `비고`: 제약, 적용 시점과 추가 설명

Requirement의 사용자, 문제, 범위와 acceptance criteria를 이 시트에 반영합니다.

### 기능 명세서 구조

| Depth 1 | Depth 2 | Depth 3 | 개발 공수(MD) | 개발 레벨 | 개발 계획 | 비고 |
| ------- | ------- | ------- | ------------- | --------- | --------- | ---- |

- 기능을 사용자 영역과 메뉴 계층에 따라 Depth로 분해합니다.
- 개발 공수, 레벨과 계획은 사용자가 요청하거나 근거가 있을 때만 작성합니다.
- 정상 흐름, Business Rule, 입력·출력, 권한, 오류와 계약은 기능 행의 비고 또는 연결된 상세 영역에 기록합니다.

## 화면 설계서

화면 설계는 Google Slides 양식을 사용하지 않고 프로젝트별 Figma Design 파일에서 관리합니다.

- `start`에서 사용자가 새 Figma Design 파일의 편집 링크를 입력합니다.
- 화면, component, variant, interaction, loading, empty, error, disabled, success와 권한 상태를 Figma에 작성합니다.
- Requirement에는 Figma file URL과 page 또는 node URL을 기록합니다.
- Figma에 직접 접근할 수 없으면 화면 명세와 반영 지시를 Requirement에 작성하고 접근할 수 있는 것처럼 표현하지 않습니다.

## DB 테이블 정의서

- 원본: [Chemtopia DB Table Definition](https://docs.google.com/spreadsheets/d/1fRYFu9aKTvfsKTkWZNLIsthRQR7a7xTHTAPn5cREiMo/edit)

전체 원본을 복사하고 다음 구조를 유지합니다.

```text
00_Overview      문서 정보와 버전
01_Table_List    table 이름과 설명 목록
NN_<table_name>  table별 정책과 column 정의
99_Indexes       unique와 index 통합 목록
```

table별 시트는 다음 내용을 포함합니다.

- Table Name과 Description
- Create, Update, Delete와 Read Policy
- 컬럼명, 데이터 타입, PK, FK, Nullable, Default, Unique, Index, 설명과 비고

`99_Indexes`는 구분, 이름, 테이블, 컬럼 또는 조건과 설명을 기록합니다. 예시 프로젝트의 table 시트와 데이터는 사본에서 제거하고 현재 프로젝트 정의로 교체합니다.

## 테스트 시나리오 및 결과서

- 원본: [Chemtopia Test Scenario](https://docs.google.com/spreadsheets/d/1Bvnh69NtpjwwwXJtgkDgjcISyXZ4IqWW1aJbm5OzSlY/edit)

전체 원본을 복사하고 다음 구조를 유지합니다.

```text
Overview                 문서 정보와 버전
테스트 시나리오 목록     기능 계층, 시나리오 ID, 제목과 목적
테스트 케이스 및 결과    사전 조건, 예상 결과, 실제 결과와 비고
```

### 테스트 시나리오 목록 구조

| Depth 1 | Depth 2 | Depth 3 | 시나리오 ID | 시나리오 제목 | 테스트 목적 |
| ------- | ------- | ------- | ----------- | ------------- | ----------- |

### 테스트 케이스 및 결과 구조

| 구분 | 시나리오 ID | 시나리오 제목 | TC ID | TC 제목 | 사전 조건 | 예상 결과 | 결과(P/F) | 비고 |
| ---- | ----------- | ------------- | ----- | ------- | --------- | --------- | --------- | ---- |

- 테스트 계획 단계에서 시나리오, 케이스, 사전 조건과 예상 결과를 작성합니다.
- 새 프로젝트 사본에는 `예상 결과` 뒤에 `실제 결과`, `증거`, `결함·재검증` column을 추가합니다.
- 구현 후 실제 결과, 결과(P/F), 실행 증거, 결함과 재검증 내용을 기록합니다.
- 원본의 완료 결과와 프로젝트 데이터는 사본에서 제거하고 새 프로젝트 결과로 교체합니다.

## 공통 규칙

- 프로젝트 산출물 링크와 정확한 sheet, range, Figma page 또는 node는 `customs/PROJECT.md`와 관련 Requirement에 기록합니다.
- 저장소 Requirement가 구현 source of truth이고 외부 산출물은 검토와 공유를 위한 동기화 결과입니다.
- 산출물을 갱신할 때 원본 양식의 제목, column 순서, formatting, validation과 식별자 체계를 유지합니다.
- 원본 양식에 현재 Requirement를 표현할 필드가 없으면 의미를 누락하지 말고 사본에 필요한 column 또는 상세 영역을 추가합니다.
- 두 내용이 충돌하면 Requirement를 기준으로 원인을 확인하고 같은 작업에서 외부 산출물을 정렬합니다.
