# Spring Data JPA Standards

## 목적

`standards/backend/spring-boot/spring-data-jpa/`는 Requirement에서 Spring Data JPA를 persistence 기술로 선택한 프로젝트에 적용할 entity, repository, query, transaction과 테스트 규칙을 정의합니다.

## 문서

| 문서                                           | 내용                                  |
| ---------------------------------------------- | ------------------------------------- |
| `BE-JPA-01-entity-convention.md`               | Entity identity, relation과 상태 변경 |
| `BE-JPA-02-entity-lifecycle-convention.md`     | Entity callback과 식별자 생명주기     |
| `BE-JPA-03-repository-convention.md`           | Repository 경계                        |
| `BE-JPA-04-query-convention.md`                | Query, pagination과 성능               |
| `BE-JPA-05-transaction-convention.md`          | Transaction, lock과 동시성             |
| `BE-JPA-06-testing-convention.md`              | Mapping, query와 실제 Database 검증    |
| `BE-JPA-07-programmatic-transaction-convention.md` | TransactionTemplate의 제한적 사용 조건 |
