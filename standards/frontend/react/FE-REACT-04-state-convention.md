# React State Convention

## 상태 소유권

- **STD-FE-REACT-040** interaction을 소유한 가장 가까운 component가 local UI state를 소유합니다.
- **STD-FE-REACT-041** 공유하거나 새로고침·뒤로 가기로 복원해야 하는 filter, page와 선택은 URL state로 표현합니다.
- **STD-FE-REACT-042** server data는 server-state 계층이 소유하며 일반 global store에 복제하지 않습니다.
- **STD-FE-REACT-043** cross-feature client state는 실제 공유 범위가 확인된 경우에만 최소 범위 provider 또는 store로 승격합니다.
- **STD-FE-REACT-044** 같은 값을 local, URL, server와 global state에 중복 저장하지 않고 하나의 source of truth에서 파생합니다.
- **STD-FE-REACT-045** persisted client state에는 schema version, migration 또는 안전한 초기화 정책을 둡니다.
- **STD-FE-REACT-046** 권한과 비즈니스 invariant를 client state로 재정의하지 않습니다.
