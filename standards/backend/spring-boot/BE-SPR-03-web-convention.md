# Spring Boot Web Convention

## Controller와 DTO

- **STD-BE-SPR-030** Controller는 HTTP mapping, 인증 주체 전달, 입력 검증과 응답 변환만 담당합니다.
- **STD-BE-SPR-031** Controller에서 repository, persistence entity 또는 외부 SDK를 직접 사용하지 않습니다.
- **STD-BE-SPR-032** API 요청과 응답은 전용 DTO로 정의하고 persistence entity를 직렬화하지 않습니다.
- **STD-BE-SPR-033** DTO field 이름, nullable, enum과 시간 표현은 Requirement의 기능 명세와 계약에 일치시킵니다.

## Validation과 오류

- **STD-BE-SPR-034** 형식과 단일 입력 제약은 Bean Validation으로 검증하고 여러 Aggregate에 걸친 비즈니스 규칙은 domain 또는 application 계층에서 검증합니다.
- **STD-BE-SPR-035** validation 오류는 field 또는 대상, 안정적인 오류 코드와 사용자 수정에 필요한 정보로 변환합니다.
- **STD-BE-SPR-036** 전역 예외 처리는 `@RestControllerAdvice`에 집중하고 같은 예외를 Controller마다 중복 변환하지 않습니다.
- **STD-BE-SPR-037** framework와 stack trace 정보를 외부 오류 응답에 노출하지 않습니다.
- **STD-BE-SPR-038** 예상 가능한 domain 실패를 일관된 HTTP status와 Requirement의 오류 계약에 mapping합니다.
