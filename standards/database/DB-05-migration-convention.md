# Database Migration Convention

## 파일과 이력

- **STD-DB-050** 실행 가능한 schema의 source of truth는 순서가 고정된 versioned migration입니다.
- **STD-DB-051** 하나의 migration은 하나의 설명 가능한 schema 또는 기준 데이터 변경 목적을 가집니다.
- **STD-DB-052** 적용된 migration을 수정, 삭제하거나 순서를 바꾸지 않습니다.
- **STD-DB-053** 자동 생성 migration도 object 이름, lock, 데이터 손실과 불필요한 변경을 검토한 뒤 반영합니다.
- **STD-DB-054** 환경별 조건문으로 서로 다른 schema를 만들지 않습니다.

## 변경 절차

- **STD-DB-055** migration 작성 전에 현재 및 선행 Requirement의 기능, 계약과 Database 설계 영향을 확인합니다.
- **STD-DB-056** 호환성, lock, 실행 시간, 저장 공간, 데이터 변환과 복구 위험을 분석합니다.
- **STD-DB-057** migration은 빈 Database와 지원하는 기존 version에서 모두 적용을 검증합니다.
- **STD-DB-058** 배포 중 구버전과 신버전 application이 공존할 수 있는지 확인하고 배포 순서를 정의합니다.
- **STD-DB-059** 가능한 경우 expand → migrate/backfill → switch → contract 순서로 호환 가능한 변경을 수행합니다.
