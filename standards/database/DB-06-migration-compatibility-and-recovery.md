# Database Migration Compatibility And Recovery

## 호환성과 복구

- **STD-DB-060** 대량 backfill은 schema 변경과 분리하고 batch, 중단, 재시작과 진행 확인 방법을 둡니다.
- **STD-DB-061** column 삭제, type 축소와 constraint 강화는 기존 데이터와 구버전 application을 준비한 뒤 수행합니다.
- **STD-DB-062** 대형 table 변경은 예상 row 수, lock 수준, 실행 시간과 추가 저장 공간을 검토합니다.
- **STD-DB-063** 긴 transaction, table rewrite와 service 중단 가능성을 배포 전에 확인하고 timeout과 중단 기준을 정합니다.
- **STD-DB-064** rollback은 down migration만을 의미하지 않으며 backup, point-in-time recovery, forward fix와 application rollback을 함께 검토합니다.
- **STD-DB-065** 비가역 변환이나 데이터 삭제 전에 복구 가능 여부, 보존 기간과 승인된 실행 절차를 확인합니다.
- **STD-DB-066** 실패한 migration의 재실행 안전성과 수동 복구 절차를 정의합니다.
