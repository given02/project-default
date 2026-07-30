# Frontend Framework Convention

- Owner: Frontend Developer
- Purpose: component, hook와 rendering 규칙을 정의합니다.
- Audience: Frontend Developer
- Dependencies: `project-environment.md`, `folder-structure.md`
- Next Reading: `typescript-convention.md`

## Framework

{{FRAMEWORK_NAME_AND_VERSION}}

## Component

- component는 하나의 명확한 UI 책임을 가집니다.
- route-level, feature, reusable UI component를 구분합니다.
- side effect는 lifecycle과 cleanup이 명확한 위치에서 처리합니다.
- 파생 가능한 값을 불필요하게 state에 중복 저장하지 않습니다.

## Hook 또는 Composition

- 재사용되는 stateful interaction은 project framework의 composition 방식으로 분리합니다.
- hook/composable은 UI markup보다 로직과 state composition을 담당합니다.
- 호출 규칙을 위반하거나 조건부 lifecycle을 만들지 않습니다.

## 성능

- 측정 없이 광범위한 memoization을 추가하지 않습니다.
- 큰 목록, 이미지, 그래프와 heavy component는 실제 병목에 따라 최적화합니다.
- loading, empty, error와 partial 상태를 명시적으로 구현합니다.
