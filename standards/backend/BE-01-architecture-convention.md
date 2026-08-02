# Backend Architecture Convention

## 구성

- **STD-BE-010** Backend 코드는 기술 계층만이 아니라 기능 또는 도메인 소유권이 드러나도록 구성합니다.
- **STD-BE-011** 여러 기능이 실제로 공유하지 않는 코드를 `common`, `shared` 또는 `util` 영역으로 이동하지 않습니다.
- **STD-BE-012** 공통 영역에는 특정 도메인의 비즈니스 규칙을 두지 않습니다.

## 계층 책임

- **STD-BE-013** Interface 계층은 외부 요청과 응답의 변환, 입력 형식 검증과 application use case 호출을 담당합니다.
- **STD-BE-014** Interface 계층은 repository를 직접 호출하거나 비즈니스 규칙을 구현하지 않습니다.
- **STD-BE-015** Application 계층은 use case, transaction boundary와 domain 및 외부 port의 orchestration을 담당합니다.
- **STD-BE-016** Domain 계층은 비즈니스 invariant와 의미 있는 상태 변경을 소유하며 framework와 전달 형식에 의존하지 않습니다.
- **STD-BE-017** Infrastructure 계층은 persistence와 외부 시스템 adapter를 구현하고 외부 모델을 내부 계약으로 누출하지 않습니다.

## 모델 경계

- **STD-BE-018** API 요청·응답 모델, domain model과 persistence model의 책임을 구분합니다.
- **STD-BE-019** persistence entity나 외부 SDK 모델을 API 응답으로 직접 노출하지 않습니다.
