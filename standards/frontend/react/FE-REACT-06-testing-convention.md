# React Testing Convention

## 기준

- **STD-FE-REACT-060** Component 테스트는 내부 state와 함수 호출보다 사용자가 보는 내용과 수행하는 interaction을 검증합니다.
- **STD-FE-REACT-061** element 조회는 가능한 경우 role, label과 accessible name을 사용하고 DOM 구조나 CSS class에 의존하지 않습니다.
- **STD-FE-REACT-062** 사용자 interaction은 실제 event 순서와 비동기 갱신을 반영하는 방식으로 실행합니다.
- **STD-FE-REACT-063** API 경계는 transport 수준에서 mock하고 실제 계약과 같은 요청, 응답과 오류 fixture를 사용합니다.
- **STD-FE-REACT-064** loading, empty, error, disabled, success와 권한 상태를 화면 명세에 따라 검증합니다.
- **STD-FE-REACT-065** routing 동작은 실제 router context에서 path, parameter, navigation과 보호 route 결과를 검증합니다.
- **STD-FE-REACT-066** Hook을 component 생명주기 밖에서 직접 실행하지 않고 필요한 provider와 cleanup을 포함한 환경에서 검증합니다.
- **STD-FE-REACT-067** snapshot만으로 동작을 검증하지 않으며 snapshot은 작고 안정적인 출력의 보조 검증으로만 사용합니다.
- **STD-FE-REACT-068** 핵심 사용자 흐름은 Backend 계약과 연결된 통합 또는 end-to-end 테스트로 검증합니다.
