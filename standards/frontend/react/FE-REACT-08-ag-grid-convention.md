# React AG Grid Community Convention

## 적용 조건과 선택

- **STD-FE-REACT-080** 일반 목록, 정렬, 필터와 pagination은 Ant Design Table을 우선하고, 대량 행 rendering, 복합 정렬·필터, cell 편집 또는 column 고정처럼 일반 Table로 충족하기 어려운 요구사항이 있을 때만 AG Grid Community를 선택합니다.
- **STD-FE-REACT-081** AG Grid Community를 선택하면 관련 Requirement에 선택 이유, 예상 data 규모, 필요한 grid 기능과 client/server 처리 경계를 기록합니다.
- **STD-FE-REACT-082** AG Grid는 Community edition만 사용하며 `ag-grid-enterprise` package와 Enterprise 전용 module 또는 기능을 설치하거나 import하지 않습니다.

## Theme과 UI 일관성

- **STD-FE-REACT-083** 화면 설계에서 확정한 색상, typography, spacing, radius와 상태 token을 AG Grid Theme API parameter로 매핑하고 Ant Design과 별도의 임의 token 체계를 만들지 않습니다.
- **STD-FE-REACT-084** grid 주변의 Button, Input, Select, Modal과 feedback UI는 선택된 Ant Design component를 사용하고 같은 화면에서 동일 목적의 Ant Design Table과 AG Grid를 중복 사용하지 않습니다.
- **STD-FE-REACT-085** 색상, font, spacing, row height와 header height는 공식 Theme API와 공개 parameter를 사용하며 내부 DOM 구조나 비공개 CSS class에 의존하지 않습니다.

## Data와 검증

- **STD-FE-REACT-086** row identity는 index가 아닌 domain의 안정적인 식별자로 제공하고 column definition과 event payload에는 명시적인 TypeScript type을 사용합니다.
- **STD-FE-REACT-087** 정렬, 필터, pagination, selection과 편집 상태의 소유권을 정하고 server-side 처리는 Requirement의 API 요청·응답 및 오류 계약에 맞춥니다.
- **STD-FE-REACT-088** loading, empty, error, no-result, disabled와 권한 상태를 화면 명세에 따라 표현하고 keyboard navigation, focus와 accessible name을 실제 사용자 흐름에서 검증합니다.
- **STD-FE-REACT-089** 대표 정렬·필터·선택·편집 흐름과 server 요청 변환을 사용자 관점 테스트로 검증하고 AG Grid 내부 구현 세부사항을 assertion 대상으로 삼지 않습니다.
