# PostgreSQL Index Convention

## 기준

- **STD-DB-PG-030** 일반 equality, range와 정렬 query에는 B-tree를 기본으로 검토합니다.
- **STD-DB-PG-031** 복합 B-tree index의 선두 column은 실제 equality, range와 sort 조건 순서를 근거로 선택합니다.
- **STD-DB-PG-032** partial index의 predicate는 실제 query 조건과 일치시키고 해당 조건을 사용하지 않는 query에 효과를 기대하지 않습니다.
- **STD-DB-PG-033** expression index를 사용하면 application query가 동일한 expression을 사용하도록 검증합니다.
- **STD-DB-PG-034** `jsonb`, array와 전문 검색에 GIN 등 특수 index를 사용할 때 operator와 쓰기 비용을 실제 query로 검증합니다.
- **STD-DB-PG-035** covering 목적의 included column은 heap 접근 감소 효과와 index 크기 증가를 측정한 뒤 사용합니다.
- **STD-DB-PG-036** production 대형 table에 index를 추가할 때는 `CREATE INDEX CONCURRENTLY` 적용 가능성과 transaction 제약을 검토합니다.
- **STD-DB-PG-037** 실패한 concurrent index 생성 뒤 invalid index가 남았는지 확인하고 재시도 전에 정리합니다.
- **STD-DB-PG-038** index 효과는 `EXPLAIN (ANALYZE, BUFFERS)` 등 실제 실행 정보와 대표 데이터에서 확인하되 production의 변경 query 실행 위험을 통제합니다.
- **STD-DB-PG-039** 사용되지 않는 index는 통계 기간, 쓰기 비용과 제약 지원 여부를 확인한 migration으로 제거합니다.
