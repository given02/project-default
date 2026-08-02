# Backend Model Boundary Convention

## 기준

- **STD-BE-020** 계층 간 변환 위치는 호출 경계에 두고 동일한 변환을 여러 계층에 중복 구현하지 않습니다.
- **STD-BE-021** 여러 domain 또는 외부 시스템에 걸친 orchestration은 application 계층에 두고 Customs의 시스템 아키텍처에 책임과 실패 처리를 정의합니다.
