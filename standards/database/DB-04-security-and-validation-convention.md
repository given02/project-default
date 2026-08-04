# Database Security And Validation Convention

## 기준

- **STD-DB-040** application, migration, 조회와 운영 계정은 최소 권한으로 분리합니다.
- **STD-DB-041** credential과 개인정보를 migration, fixture와 log에 평문으로 저장하지 않습니다.
- **STD-DB-042** 개인정보 column에는 접근, 암호화 또는 hash, masking, log와 보존 정책을 연결합니다.
- **STD-DB-043** 중요한 query는 실제 또는 대표 데이터 분포에서 실행 계획을 검토합니다.
- **STD-DB-044** 운영 Database에서 검토되지 않은 수동 DDL을 실행하지 않습니다.
- **STD-DB-045** Requirement의 Database 설계에는 새로 만들거나 변경하는 모든 table과 column의 의미, type, key, nullable과 default를 빠짐없이 정의합니다.
- **STD-DB-046** constraint와 index는 실제 존재하는 table과 column만 참조하며 table별 정의와 전체 schema 사이에 불일치를 허용하지 않습니다.
- **STD-DB-047** 생성, 수정, 삭제, 보존과 복구 정책은 Requirement의 기능 및 Database 설계와 일치하고 constraint 및 migration에 같은 의미로 반영합니다.
- **STD-DB-048** 개인정보와 민감정보 column을 명시적으로 식별하고 각 column에 접근과 보호 정책을 연결합니다.
- **STD-DB-049** schema 변경은 관련 constraint, index, migration, 주요 query와 application 통합 동작을 함께 검증합니다.
