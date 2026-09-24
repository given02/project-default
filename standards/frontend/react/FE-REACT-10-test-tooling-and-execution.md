# React Test Tooling and Execution

## 기본 도구

- **STD-FE-REACT-100** React와 TypeScript의 Component·UI 통합 테스트 기본 조합은 Vitest, React Testing Library와 필요한 `@testing-library/dom` peer dependency, `@testing-library/user-event`, `@testing-library/jest-dom`입니다. 실제 프로젝트는 호환되는 version을 개발 dependency와 lockfile에 고정합니다.
- **STD-FE-REACT-101** DOM 테스트는 Vitest의 `jsdom` 환경을 사용하고 공통 setup에서 `@testing-library/jest-dom/vitest`를 등록합니다. `jsdom`, router, provider와 상태 저장소는 테스트에 필요한 범위에서만 구성합니다.
- **STD-FE-REACT-102** Vitest는 `src`의 `*.test.ts`와 `*.test.tsx`만 수집하고 `*.e2e.spec.ts`는 제외합니다. TypeScript와 production build 설정도 테스트 파일이 runtime bundle에 포함되지 않도록 검증합니다.

## 경계와 격리

- **STD-FE-REACT-103** API를 호출하는 Component·UI 통합 테스트는 MSW로 HTTP 경계를 대체합니다. 처리되지 않은 요청은 오류로 보고하고 테스트마다 handler를 초기화합니다. 응답 fixture는 Requirement의 API 계약과 함께 갱신합니다.
- **STD-FE-REACT-104** 테스트는 서로의 router, store, local storage, timer, mock과 network handler 상태를 공유하지 않습니다. 비동기 화면 검증은 `findBy`·`waitFor`처럼 결과를 기다리는 assertion을 사용합니다.

## Browser E2E

- **STD-FE-REACT-105** 실제 browser, navigation 또는 여러 화면과 Backend 경계를 확인해야 하는 Requirement에서만 Playwright를 추가합니다. Playwright는 `src`에서 `*.e2e.spec.ts`만 수집하고 Component 테스트는 수집하지 않습니다.
- **STD-FE-REACT-106** E2E 테스트는 실행 중인 Frontend와 검증 목적에 맞는 Backend 또는 통제된 test server를 대상으로 합니다. API를 mock한 browser 테스트는 UI 통합 테스트로 표시하고 실제 Backend 통합을 검증한 것으로 보고하지 않습니다.
- **STD-FE-REACT-107** E2E 테스트는 role·label 기반 locator와 자동 대기 assertion을 사용하고 고정 sleep과 CSS 구조에 의존하지 않습니다. 필요한 server 시작, base URL과 독립 test data는 Playwright 설정 또는 테스트 준비 절차로 재현 가능하게 합니다.

## 실행과 완료

- **STD-FE-REACT-108** 프로젝트의 `test` script는 watch 없는 Vitest 전체 실행을, Playwright를 사용하는 경우 `test:e2e` script는 browser 테스트 실행을 담당합니다. CI는 `test`를 실행하고 E2E가 적용되는 Requirement의 검증 단계에서는 `test:e2e`도 실행합니다.
- **STD-FE-REACT-109** Frontend Developer는 변경한 사용자 동작과 주요 실패·권한 경로를 대응 테스트로 검증하고, 실행한 명령·결과·실행하지 못한 이유를 Requirement에 기록한 뒤 Review로 전환합니다. 커버리지 숫자만으로 완료를 판정하지 않습니다.
