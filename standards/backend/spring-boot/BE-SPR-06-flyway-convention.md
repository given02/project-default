# Spring Boot Flyway Convention

## 적용과 Source Of Truth

- **STD-BE-SPR-060** Spring Boot에서 관계형 Database를 사용하면 Flyway를 schema migration 도구로 사용합니다.
- **STD-BE-SPR-061** 실행 가능한 schema의 source of truth는 Flyway migration이며 Hibernate `ddl-auto`는 `validate` 또는 `none`만 사용하고 `create`, `create-drop` 또는 `update`로 schema를 생성하거나 변경하지 않습니다.
- **STD-BE-SPR-062** versioned migration은 `src/main/resources/db/migration` 아래에 `V<version>__<description>.sql` 형식으로 두고 version 순서와 설명 가능한 변경 목적을 유지합니다.
- **STD-BE-SPR-063** 한 번 적용된 versioned migration은 수정하거나 삭제하지 않고 오류 수정과 추가 변경은 새 migration으로 작성합니다.
- **STD-BE-SPR-064** repeatable migration은 view, function처럼 전체 정의를 안전하게 다시 적용할 수 있는 객체에만 사용하고 순차적인 schema 변경을 대신하지 않습니다.

## 데이터와 실행

- **STD-BE-SPR-065** schema와 필수 기준 데이터만 Flyway migration에 포함하고 sample, 개발 및 테스트 전용 데이터는 분리합니다.
- **STD-BE-SPR-066** application 계정과 migration 계정의 권한을 가능한 범위에서 분리하고 migration에 credential이나 환경별 비밀값을 포함하지 않습니다.
- **STD-BE-SPR-067** transaction block에서 실행할 수 없는 DDL은 별도 migration으로 분리하고 Flyway와 대상 Database의 transaction 실행 방식을 명시적으로 구성합니다.

## 검증

- **STD-BE-SPR-068** Flyway migration은 production과 호환되는 실제 Database에서 빈 schema와 지원하는 이전 schema 모두를 대상으로 순차 적용을 검증합니다.
- **STD-BE-SPR-069** application 시작 검증에서 Flyway migration 성공과 허용되지 않은 pending 또는 failed migration 부재를 확인하고, JPA를 사용하면 mapping과 schema의 일치도 검증합니다.
