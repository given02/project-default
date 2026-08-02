# React Component Convention

## Component

- **STD-FE-REACT-020** Component는 하나의 명확한 UI 책임을 가지며 route, feature와 재사용 UI 역할을 구분합니다.
- **STD-FE-REACT-021** render 중에는 외부 상태 변경, network 요청과 비결정적 side effect를 수행하지 않습니다.
- **STD-FE-REACT-022** props는 component가 필요한 최소 계약을 표현하고 서로 모순되는 boolean 조합보다 명확한 variant를 사용합니다.
- **STD-FE-REACT-023** props와 server data에서 계산할 수 있는 값을 state에 중복 저장하지 않습니다.
- **STD-FE-REACT-024** list의 key는 항목 identity를 안정적으로 나타내야 하며 순서가 바뀔 수 있는 목록에 index를 identity로 사용하지 않습니다.

## Hook과 Effect

- **STD-FE-REACT-025** 재사용되는 stateful interaction은 custom Hook으로 분리하고 Hook은 UI markup을 반환하지 않습니다.
- **STD-FE-REACT-026** Hook 호출 규칙을 지키며 조건문, 반복문과 중첩 함수 안에서 Hook을 호출하지 않습니다.
- **STD-FE-REACT-027** Effect는 외부 시스템과 동기화할 때만 사용하고 render에서 계산 가능한 상태를 맞추는 용도로 사용하지 않습니다.
- **STD-FE-REACT-028** Effect가 subscription, timer와 request 같은 자원을 만들면 cleanup과 stale 결과 처리를 구현합니다.
- **STD-FE-REACT-029** Effect dependency를 경고 억제로 누락하지 않고 불안정한 의존성은 책임과 데이터 흐름을 다시 구성합니다.
