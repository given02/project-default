# Persistence Convention

## 경계와 Mapping

- **STD-BE-050** 물리 schema와 제품의 domain model을 같은 것으로 간주하지 않습니다.
- **STD-BE-051** persistence model을 API 계약으로 직접 사용하지 않습니다.
- **STD-BE-052** persistence 편의를 위해 domain invariant를 약화하거나 외부 라이브러리 및 Database 전용 타입을 domain에 노출하지 않습니다.
- **STD-BE-053** identifier, nullable, enum과 시간 mapping은 Customs의 domain model 및 database schema와 일치시킵니다.

## 조회

- **STD-BE-054** repository 또는 query port는 저장 기술보다 호출자의 조회 의도를 드러내는 인터페이스를 제공합니다.
- **STD-BE-055** N+1, 무제한 조회와 필요하지 않은 eager loading을 허용하지 않습니다.
- **STD-BE-056** 대량 목록은 Customs의 API 및 데이터 설계에 정의된 pagination, cursor 또는 streaming 방식을 사용합니다.
- **STD-BE-057** projection과 전용 조회 모델은 읽기 목적에 사용할 수 있지만 domain invariant를 변경하는 쓰기 경로로 사용하지 않습니다.
- **STD-BE-058** 중요한 query는 실제 접근 패턴, 대표 데이터 분포와 Database index를 함께 검토합니다.
