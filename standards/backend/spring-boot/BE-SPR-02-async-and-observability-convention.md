# Spring Boot Async And Observability Convention

## 기준

- **STD-BE-SPR-020** `@Async`, scheduler와 event listener를 사용하면 실행 주체, transaction 경계, 실패, 재시도와 중복 실행 영향을 명시합니다.
- **STD-BE-SPR-021** application event를 신뢰성 있는 외부 메시지 전달이나 transaction 보장 수단으로 사용하지 않습니다.
- **STD-BE-SPR-022** health check는 프로세스 생존과 실제 트래픽 수용 가능성을 구분하고 민감한 내부 정보를 노출하지 않습니다.
