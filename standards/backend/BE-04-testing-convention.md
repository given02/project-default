# Backend Testing Convention

## 기준

- **STD-BE-040** 비즈니스 규칙은 단위 테스트로, persistence와 외부 연동은 실제 경계를 사용하는 통합 테스트로 검증합니다.
- **STD-BE-041** API 테스트는 성공, validation, 인증, 권한, not-found와 계약에 정의된 주요 오류를 검증합니다.
- **STD-BE-042** Service와 application use case의 새 비즈니스 동작은 production code보다 실패하는 단위 테스트를 먼저 작성합니다.
- **STD-BE-043** Service 단위 테스트는 framework context를 시작하지 않고 repository, 외부 API와 메시지 같은 외부 경계를 mock 또는 fake로 대체합니다.
- **STD-BE-044** Service의 정상 결과와 주요 실패 조건은 각각 독립된 테스트로 작성하고 하나의 테스트는 하나의 비즈니스 결과만 검증합니다.
- **STD-BE-045** 실패 테스트가 의도한 미구현 동작 때문에 실패하는지 확인한 뒤 이를 통과시키는 최소 코드를 작성하고, 통과 상태에서 책임 분리와 중복 제거를 수행합니다.
- **STD-BE-046** 하나의 실패 조건은 이를 판단하는 Service 또는 domain 책임의 테스트가 소유하며 Controller와 persistence 계층에서 같은 비즈니스 판단을 중복하지 않습니다.
- **STD-BE-047** private method를 직접 테스트하지 않으며 독립적인 비즈니스 책임이면 별도 domain object나 policy로 추출해 공개 동작으로 검증합니다.
- **STD-BE-048** Controller는 비즈니스 규칙을 소유하지 않고 HTTP mapping, 입력 validation, 인증 주체 전달, Service 결과와 오류의 응답 변환만 검증합니다.
- **STD-BE-049** Repository의 기본 CRUD를 반복 검증하지 않고 custom query, mapping, constraint와 transaction처럼 실제 persistence 의미가 중요한 동작만 통합 테스트합니다.
