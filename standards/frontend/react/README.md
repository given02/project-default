# React Standards

## 목적

`standards/frontend/react/`는 Requirement에서 React와 TypeScript를 Frontend 기술로 선택한 프로젝트에 적용할 고정 구현 규칙을 정의합니다.

## 문서

| 문서                                          | 내용                                 |
| --------------------------------------------- | ------------------------------------ |
| `FE-REACT-01-project-structure.md`            | 폴더와 feature 소유권                |
| `FE-REACT-02-component-convention.md`         | Component, Hook와 rendering          |
| `FE-REACT-03-rendering-performance-convention.md` | Rendering 성능과 Error Boundary  |
| `FE-REACT-04-state-convention.md`             | 상태 분류와 소유권                    |
| `FE-REACT-05-routing-convention.md`           | URL과 route                           |
| `FE-REACT-06-testing-convention.md`           | 사용자 중심 component 및 통합 테스트 |
| `FE-REACT-07-ant-design-convention.md`        | Ant Design 선택, theme과 component 사용 |
| `FE-REACT-08-ag-grid-convention.md`           | AG Grid Community 선택, theme과 data grid 구현 |
| `FE-REACT-09-test-source-layout.md`           | Component·E2E 테스트 위치와 실행 결과     |
| `FE-REACT-10-test-tooling-and-execution.md`   | Vitest, MSW, Playwright와 실행·검증       |
| `FE-TS-01-type-safety-convention.md`          | TypeScript type 안전성                |
| `FE-TS-02-contract-and-generation-convention.md` | API type과 생성 코드               |

Ant Design과 AG Grid Community는 모든 React 프로젝트의 필수 dependency가 아닙니다. Requirement가 각 library를 선택한 경우에만 대응 문서가 의무 Standard로 적용됩니다. 업무·관리 화면은 Ant Design을 기본 후보로 검토하고, AG Grid Community는 일반 Table로 충족할 수 없는 data grid 요구사항에만 사용합니다.
