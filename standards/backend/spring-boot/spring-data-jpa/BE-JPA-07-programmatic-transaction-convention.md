# JPA Programmatic Transaction Convention

## TransactionTemplate 사용 조건

- **STD-BE-JPA-070** `TransactionTemplate`은 하나의 method 안에서 transaction의 시작과 종료 범위를 명시적으로 제어해야 하고 별도 application service method로 나누는 것보다 그 범위가 더 명확할 때만 사용합니다. 단순한 use case 전체 transaction에는 **STD-BE-JPA-050**의 `@Transactional`을 사용합니다.
- **STD-BE-JPA-071** `@Transactional`의 self-invocation 문제를 우회하려는 목적으로 `TransactionTemplate`을 도입하지 않습니다. transaction 경계가 다른 use case는 별도 Spring-managed application service의 public method로 분리하고 경계와 rollback 동작을 테스트합니다.
