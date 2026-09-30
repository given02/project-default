# JPA Transaction Convention

## 기준

- **STD-BE-JPA-050** 하나의 use case가 하나의 transaction을 사용하면 application service의 public 진입점에 `@Transactional`을 두는 선언적 방식을 기본으로 사용합니다.
- **STD-BE-JPA-051** private method나 self-invocation에 proxy transaction 동작을 기대하지 않습니다.
- **STD-BE-JPA-052** 읽기 전용 use case에는 `readOnly = true`를 사용하되 routing이나 최적화 효과를 환경별로 검증합니다.
- **STD-BE-JPA-053** transaction 안에서 HTTP, message broker와 file storage 같은 외부 네트워크 작업을 불필요하게 수행하지 않습니다.
- **STD-BE-JPA-054** lazy loading을 Controller 직렬화 단계까지 미루지 않고 transaction 안에서 필요한 데이터를 명시적으로 조회하고 변환합니다.
- **STD-BE-JPA-055** Open EntityManager In View에 의존해 계층 경계 밖의 lazy loading을 허용하지 않습니다.
- **STD-BE-JPA-056** optimistic lock은 충돌을 사용자 또는 재시도 정책으로 처리할 수 있는 경우 사용하고 무제한 자동 재시도하지 않습니다.
- **STD-BE-JPA-057** pessimistic lock은 경쟁 조건과 lock 범위를 확인하고 일관된 획득 순서, timeout과 실패 처리를 정의합니다.
- **STD-BE-JPA-058** bulk update와 delete 후에는 persistence context의 stale entity 영향을 제거하거나 격리합니다.
- **STD-BE-JPA-059** transaction rollback 동작을 예외 catch와 변환 과정에서 무효화하지 않으며 필요한 rollback 조건을 테스트합니다.
