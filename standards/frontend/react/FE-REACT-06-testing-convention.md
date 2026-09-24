# React Testing Convention

## 기준

- **STD-FE-REACT-060** Component 테스트는 내부 state와 함수 호출보다 사용자가 보는 내용과 수행하는 interaction을 검증합니다. 하나의 테스트는 설명 가능한 사용자 결과 하나를 중심으로 작성합니다.
- **STD-FE-REACT-061** element 조회는 role과 accessible name, form label을 우선 사용합니다. DOM 구조나 CSS class에 의존하지 않고 `data-testid`는 의미 있는 접근성 조회가 불가능할 때만 사용합니다.
- **STD-FE-REACT-062** 사용자 interaction은 테스트마다 생성한 `userEvent` instance로 실행하고 비동기 동작을 기다립니다. 지원되지 않는 세부 event에만 `fireEvent`를 사용하며 임의의 고정 sleep으로 화면 갱신을 기다리지 않습니다.
- **STD-FE-REACT-063** API 경계는 transport 수준에서 mock하고 실제 계약과 같은 요청, 응답과 오류 fixture를 사용합니다.
- **STD-FE-REACT-064** 변경한 사용자 동작에 관련된 loading, empty, error, disabled, success와 권한 상태를 화면 명세에 따라 검증합니다. 모든 상태를 모든 Component에 기계적으로 복제하지 않습니다.
- **STD-FE-REACT-065** routing 동작은 실제 router context에서 path, parameter, navigation과 보호 route 결과를 검증합니다.
- **STD-FE-REACT-066** Hook을 component 생명주기 밖에서 직접 실행하지 않고 필요한 provider와 cleanup을 포함한 환경에서 검증합니다.
- **STD-FE-REACT-067** snapshot만으로 동작을 검증하지 않으며 snapshot은 작고 안정적인 출력의 보조 검증으로만 사용합니다.
- **STD-FE-REACT-068** 핵심 사용자 흐름은 Backend 계약과 연결된 통합 또는 end-to-end 테스트로 검증합니다.
- **STD-FE-REACT-069** 테스트 이름은 사용자 행동 또는 조건과 관찰 가능한 결과를 드러냅니다. 순수한 표현 변경만 있고 동작과 접근성 계약이 그대로라면 중복 테스트를 추가하지 않습니다.
