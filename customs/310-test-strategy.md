# Test Strategy

## 목표와 범위

- 테스트가 보장해야 하는 핵심 사용자 결과: 작성 필요
- 가장 위험한 Business Rule과 경계: 작성 필요
- 자동화하지 않는 검증과 이유: 해당 없음 또는 작성 필요

## Test 수준

| 수준                 | 대상                         | 도구      | 실행 환경 | 필수 범위 |
| -------------------- | ---------------------------- | --------- | --------- | --------- |
| Unit                 | 작성 필요                    | 작성 필요 | 작성 필요 | 작성 필요 |
| Component 또는 Slice | 작성 필요                    | 작성 필요 | 작성 필요 | 작성 필요 |
| Integration          | 작성 필요                    | 작성 필요 | 작성 필요 | 작성 필요 |
| Contract             | 적용하지 않음 또는 작성 필요 | 작성 필요 | 작성 필요 | 작성 필요 |
| End-to-End           | 작성 필요                    | 작성 필요 | 작성 필요 | 작성 필요 |

## 영역별 검증

### Backend

- Domain과 Business Rule: 작성 필요
- API 계약과 오류: 작성 필요
- 인증과 권한: 작성 필요
- Persistence와 migration: 작성 필요
- 외부 시스템 실패: 작성 필요

### Frontend

- Component와 접근성: 작성 필요
- User Flow와 Screen 상태: 작성 필요
- API 요청과 오류 처리: 작성 필요
- Routing과 권한 UI: 작성 필요
- 지원 Browser와 viewport: 작성 필요

### Database

- 전체 migration 적용: 작성 필요
- Constraint와 index: 작성 필요
- 대표 query 실행 계획: 작성 필요
- 동시성과 lock: 작성 필요

## Test 데이터

| 항목                       | 정책      |
| -------------------------- | --------- |
| Fixture와 factory          | 작성 필요 |
| 개인정보와 운영 데이터     | 작성 필요 |
| 시간과 난수 제어           | 작성 필요 |
| Database 초기화            | 작성 필요 |
| 외부 API mock 또는 sandbox | 작성 필요 |

## Requirement 추적

| Requirement | Acceptance Criteria | 검증 수준 | Test 위치 또는 시나리오 |
| ----------- | ------------------- | --------- | ----------------------- |
| `REQ-001`   | 작성 필요           | 작성 필요 | 작성 필요               |

## 필수 검증 명령

| 시점           | 명령      | 성공 기준 |
| -------------- | --------- | --------- |
| 개발 중        | 작성 필요 | 작성 필요 |
| Task Review 전 | 작성 필요 | 작성 필요 |
| Merge 또는 CI  | 작성 필요 | 작성 필요 |
| Release 전     | 작성 필요 | 작성 필요 |

## 완료 기준

- 모든 Requirement의 Acceptance Criteria에 검증 방법이 연결됩니다.
- 실제 Database, API와 Browser가 필요한 동작을 단위 테스트만으로 대체하지 않습니다.
- 실패한 검증과 실행하지 못한 검증을 성공으로 취급하지 않습니다.
- Task가 실행할 정확한 검증 명령을 참조할 수 있습니다.
