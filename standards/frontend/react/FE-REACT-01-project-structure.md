# React Project Structure

## 기본 역할

```text
src/
├── app/          application bootstrap와 provider
├── pages/        route 단위 조합
├── features/     사용자 기능별 UI와 interaction
├── components/   둘 이상의 feature가 사용하는 UI
├── api/          공통 API client 기반
├── assets/       정적 asset
├── styles/       theme와 global style
├── types/        순환 의존성이 없는 공유 type
└── utils/        domain 의미가 없는 utility
```

실제 생성 경로와 사용하지 않는 디렉터리는 프로젝트 Bootstrap Requirement에서 확정합니다.

## 기준

- **STD-FE-REACT-010** feature 전용 component, hook, API 함수와 type은 해당 feature가 소유합니다.
- **STD-FE-REACT-011** 재사용 가능성만으로 코드를 공유 위치에 두지 않고 둘 이상의 독립 소비자가 생겼을 때 이동합니다.
- **STD-FE-REACT-012** page는 route layout과 feature 조합을 담당하고 복잡한 사용자 interaction과 제품 규칙을 feature에 위임합니다.
- **STD-FE-REACT-013** `app`은 bootstrap, 전역 provider와 최상위 route 구성을 담당하며 feature 구현을 소유하지 않습니다.
- **STD-FE-REACT-014** `components`에는 제품 기능의 상태와 API 호출을 숨기지 않고 props와 event로 필요한 계약을 드러냅니다.
- **STD-FE-REACT-015** `utils`를 도메인 로직의 임시 저장소로 사용하지 않습니다.
- **STD-FE-REACT-016** Backend 계층이나 persistence 구조를 Frontend 폴더 구조에 복제하지 않습니다.
- **STD-FE-REACT-017** feature 사이의 직접 의존성을 최소화하고 공유 계약이 필요하면 명시적인 상위 소유 위치로 이동합니다.
