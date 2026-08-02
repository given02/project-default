# Business Rules

## 작성 규칙

- 비즈니스 규칙은 구현 기술과 독립적인 조건과 결과로 작성합니다.
- 같은 규칙을 Requirement, API, Backend와 Frontend 문서에 복사하지 않고 Business Rule ID를 참조합니다.
- 규칙 변경 시 관련 Requirement, Domain, Database, API와 테스트 영향을 함께 검토합니다.

## 규칙

아래 절을 규칙마다 복사해 작성합니다.

### BR-001: 규칙 이름

| 항목             | 내용                     |
| ---------------- | ------------------------ |
| 설명             | 작성 필요                |
| 적용 대상        | 작성 필요                |
| 조건             | 작성 필요                |
| 결과             | 작성 필요                |
| 예외             | 해당 없음 또는 작성 필요 |
| 위반 시 결과     | 작성 필요                |
| 관련 Requirement | `REQ-001`                |

#### 검증 예시

| 입력 또는 상황 | 기대 결과 |
| -------------- | --------- |
| 작성 필요      | 작성 필요 |

#### 구현 영향

- Domain: 작성 필요
- Database constraint: 해당 없음 또는 작성 필요
- API validation/error: 해당 없음 또는 작성 필요
- UI validation/state: 해당 없음 또는 작성 필요

## 완료 기준

- 모든 invariant가 하나의 Business Rule ID로 식별됩니다.
- 조건, 결과, 예외와 위반 결과가 모호하지 않습니다.
- Backend와 Frontend가 같은 입력에 같은 결과를 판단할 수 있습니다.
- Database에서 보호할 규칙과 application에서 보호할 규칙이 구분됩니다.
