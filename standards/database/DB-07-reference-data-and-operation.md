# Database Reference Data And Operation

## 기준

- **STD-DB-070** application 동작에 필수인 기준 데이터와 개발용 sample 데이터를 분리합니다.
- **STD-DB-071** 기준 데이터 변경은 idempotent하고 versioned된 방식으로 관리합니다.
- **STD-DB-072** production에 sample, test account, secret과 민감한 fixture를 삽입하지 않습니다.
- **STD-DB-073** 배포 후 migration 상태, 오류, lock, query 성능과 데이터 정합성을 확인합니다.
