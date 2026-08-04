# PostgreSQL Testing Convention

## 기준

- **STD-DB-PG-050** migration과 persistence 통합 테스트는 production과 호환되는 PostgreSQL 환경에서 실행합니다.
- **STD-DB-PG-051** 빈 Database에 전체 migration을 적용하고 지원하는 기존 schema에서 최신 schema로의 순차 적용을 검증합니다.
- **STD-DB-PG-052** 실제 schema의 table, column, type, default, constraint와 index가 Requirement의 Database 설계와 일치하는지 확인합니다.
- **STD-DB-PG-053** nullable unique, partial unique, foreign key action과 check constraint의 경계 동작을 실제 PostgreSQL에서 검증합니다.
- **STD-DB-PG-054** 중요한 query는 대표 데이터 분포와 PostgreSQL 실행 계획으로 검증합니다.
- **STD-DB-PG-055** lock과 동시성 테스트는 서로 다른 connection과 transaction을 사용하고 timeout 및 실패 결과를 확인합니다.
- **STD-DB-PG-056** production dump를 테스트에 사용하면 개인정보를 비식별화하고 접근 및 보존 범위를 제한합니다.
- **STD-DB-PG-057** PostgreSQL version 차이에 영향을 받는 기능은 Bootstrap Requirement가 정한 version 범위에서 검증합니다.
