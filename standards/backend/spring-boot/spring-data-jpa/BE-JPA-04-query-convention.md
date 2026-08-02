# JPA Query Convention

## 기준

- **STD-BE-JPA-040** collection 연관관계를 무조건 fetch join하지 않고 사용 시점과 결과 크기를 기준으로 조회 전략을 정합니다.
- **STD-BE-JPA-041** collection fetch join과 pagination을 함께 사용해 메모리 pagination이나 중복 결과를 만들지 않습니다.
- **STD-BE-JPA-042** 목록 조회는 count query 비용과 필요 여부를 검토하고 반환 계약에 맞는 pagination 방식을 사용합니다.
- **STD-BE-JPA-043** 읽기 전용 화면과 보고서는 필요한 column만 반환하는 projection 또는 전용 query model을 사용할 수 있습니다.
- **STD-BE-JPA-044** native query는 Database 전용 기능이나 측정된 성능 근거가 있을 때 사용하고 결과 mapping과 portability 영향을 명시합니다.
- **STD-BE-JPA-045** query 최적화는 실제 SQL, 실행 계획과 대표 데이터 분포를 확인한 뒤 수행합니다.
- **STD-BE-JPA-046** 반복 조회 경로는 query 수를 테스트하거나 관측해 N+1 회귀를 방지합니다.
