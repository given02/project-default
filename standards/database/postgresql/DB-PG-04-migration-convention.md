# PostgreSQL Migration Convention

## 기준

- **STD-DB-PG-040** PostgreSQL의 transactional DDL을 활용하되 migration 도구와 명령별 transaction 지원 여부를 확인합니다.
- **STD-DB-PG-041** `CREATE INDEX CONCURRENTLY`처럼 transaction block에서 실행할 수 없는 명령은 별도 migration과 실행 방식으로 분리합니다.
- **STD-DB-PG-042** 대형 table에 not-null 또는 check constraint를 추가할 때는 기존 데이터 검증과 lock 영향을 분석하고 필요한 경우 단계적으로 검증합니다.
- **STD-DB-PG-043** default 추가, column type 변경과 table rewrite 가능성은 대상 PostgreSQL version과 실제 table 규모에서 확인합니다.
- **STD-DB-PG-044** 위험한 DDL에는 적절한 `lock_timeout`과 `statement_timeout`을 적용하고 timeout을 무제한으로 비활성화하지 않습니다.
- **STD-DB-PG-045** enum type, extension, function과 trigger 변경은 dependency와 rollback 또는 forward recovery 순서를 함께 검토합니다.
- **STD-DB-PG-046** 대량 데이터 변경은 작은 batch로 실행하고 primary key 또는 안정적인 cursor를 사용해 중단 후 재개할 수 있게 합니다.
- **STD-DB-PG-047** migration 후 invalid index, unvalidated constraint, sequence 값과 예상 schema를 확인합니다.
- **STD-DB-PG-048** vacuum, analyze와 통계 갱신이 필요한 대량 변경은 운영 절차와 관측 항목에 포함합니다.
