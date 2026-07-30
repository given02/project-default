# Backend Documents

## 목적

Backend 구현에만 적용되는 환경, 구조, 코드, persistence와 연동 규칙을 관리합니다.

## 문서

- `project-environment.md`: 언어, 도구, dependency와 실행 환경
- `architecture-convention.md`: package, layer와 orchestration
- `code-convention.md`: 코드와 테스트 convention
- `framework-convention.md`: 선택한 Backend framework 규칙
- `persistence-convention.md`: 애플리케이션과 persistence 계층 사이의 mapping, 조회와 transaction 규칙
- `database-convention.md`: 물리 데이터베이스 schema, 명명, 타입, 제약과 index 규칙
- `database-schema-definition.md`: 프로젝트별 테이블, 컬럼, 관계, 제약과 index 정의 양식
- `database-migration-convention.md`: schema migration, 배포, rollback과 기준 데이터 규칙
- `database-review-checklist.md`: 데이터베이스 설계와 변경 검토 기준
- `resource-lifecycle-policy.md`: 리소스 생성, 수정, 삭제 정책
- `file-storage-convention.md`: 파일 저장 기능을 사용할 경우의 규칙

적용하지 않는 선택 문서는 삭제하거나 `해당 없음`과 그 이유를 기록합니다.

## 경계

제품 요구사항, 도메인 의미와 API 계약은 `../../documents/`를 참조합니다.
