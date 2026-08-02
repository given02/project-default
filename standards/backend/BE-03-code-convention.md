# Backend Code Convention

## 명명과 책임

- **STD-BE-030** package, type, 함수와 변수 이름은 Customs 용어집의 도메인 용어와 일치시킵니다.
- **STD-BE-031** 축약어와 `data`, `info`, `manager`, `helper` 같은 범용 이름보다 구체적인 책임과 결과를 드러내는 이름을 사용합니다.
- **STD-BE-032** public 동작은 성공 결과와 예상 가능한 실패 조건이 명확해야 합니다.

## 오류

- **STD-BE-033** 예상 가능한 domain 실패와 예기치 않은 system 실패를 구분합니다.
- **STD-BE-034** infrastructure와 framework 예외를 외부 API에 직접 노출하지 않습니다.
- **STD-BE-035** API 오류는 Customs의 API 계약에 정의된 안정적인 오류 코드와 응답으로 변환합니다.
- **STD-BE-036** 예외를 잡고 무시하거나 성공 결과, 빈 값 또는 `null`로 위장하지 않습니다.

## 로그와 검증

- **STD-BE-037** 로그에는 요청과 실패를 추적할 식별자와 맥락을 포함하되 요청·응답 전체를 기본적으로 기록하지 않습니다.
- **STD-BE-038** secret, token, 인증 정보, 개인정보와 파일 원문을 로그에 기록하지 않습니다.
