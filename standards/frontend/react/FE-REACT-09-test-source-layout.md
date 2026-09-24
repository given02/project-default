# React Test Source Layout

## 위치와 실행

- **STD-FE-REACT-090** Component와 UI 통합 테스트는 검증 대상 component, feature 또는 page의 `src` 위치에 함께 두고 `*.test.ts` 또는 `*.test.tsx`로 이름을 구분합니다. 테스트 전용 최상위 directory를 기본으로 만들지 않습니다.
- **STD-FE-REACT-091** 핵심 사용자 흐름에 browser E2E 테스트가 필요한 경우 해당 흐름을 소유한 `src` feature 또는 page 가까이에 `*.e2e.spec.ts`로 둡니다. `frontend/e2e` directory를 만들지 않습니다.
- **STD-FE-REACT-092** E2E runner는 `*.e2e.spec.ts`만 찾고 Component test runner는 이 파일을 제외하도록 설정합니다. E2E test source가 production bundle에 포함되지 않는지도 확인합니다. E2E를 실행하지 않는 프로젝트에는 runner, 설정 파일이나 빈 test directory를 추가하지 않습니다.
- **STD-FE-REACT-093** test source와 fixture는 Git에 추적하고 `test-results/`, `playwright-report/`, `blob-report/` 같은 실행 결과는 `.gitignore`로 제외합니다. 테스트 실행 명령과 실제 결과는 Requirement에 기록합니다.
