# Database Column Convention

## Column

- **STD-DB-020** foreign key column은 참조 대상 key와 호환되는 type을 사용합니다.
- **STD-DB-021** 금액과 정밀 계산에는 부동소수점 type을 사용하지 않습니다.
- **STD-DB-022** 날짜, 로컬 시간과 특정 시점을 구분하고 API의 시간 표현 및 timezone 정책과 일치시킵니다.
- **STD-DB-023** boolean은 Database의 boolean type과 `true`·`false`를 사용하고 `Y`·`N`, `0`·`1`과 혼용하지 않습니다.
- **STD-DB-024** 상태 값은 자유 문자열로 방치하지 않고 check constraint, lookup table 또는 Database가 제공하는 검증 수단으로 범위를 보호합니다.
- **STD-DB-025** 대용량 binary는 기본적으로 object storage에 저장하고 Database에는 식별자와 metadata를 저장합니다.

## NULL과 Default

- **STD-DB-026** `NULL`은 값이 없거나 적용되지 않는 의미가 실제로 존재할 때만 허용합니다.
- **STD-DB-027** 빈 문자열, `0`, 임의 날짜와 `N/A`를 `NULL` 대신 sentinel로 사용하지 않습니다.
- **STD-DB-028** default는 business rule을 숨기지 않는 안전한 값에만 사용하며 생성 책임을 Database와 application에 중복으로 두지 않습니다.
- **STD-DB-029** nullable unique column과 soft delete의 중복 허용 의미가 제품 요구사항과 맞는지 검토합니다.
