# JPA Testing Convention

## 기준

- **STD-BE-JPA-060** Entity mapping, repository query와 Database constraint는 persistence 통합 테스트로 검증합니다.
- **STD-BE-JPA-061** 운영 Database와 SQL, 타입 또는 constraint 의미가 다른 in-memory Database로 중요한 persistence 동작을 대체하지 않습니다.
- **STD-BE-JPA-062** repository 테스트는 저장 성공뿐 아니라 nullable, unique, foreign key와 check constraint 실패를 필요한 범위에서 검증합니다.
- **STD-BE-JPA-063** fetch 전략이 중요한 조회는 실제 query 수 또는 생성 SQL을 검증해 N+1을 방지합니다.
- **STD-BE-JPA-064** custom query와 native query는 정렬, pagination, 빈 결과와 경계 조건을 실제 Database에서 검증합니다.
- **STD-BE-JPA-065** lock과 동시 갱신 규칙은 둘 이상의 독립 transaction을 사용한 통합 테스트로 검증합니다.
- **STD-BE-JPA-066** 테스트가 transaction rollback에 가려 production flush 시점의 constraint 오류를 놓치지 않도록 필요한 지점에서 flush합니다.
