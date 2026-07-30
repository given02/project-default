# Backend Code Convention

- Owner: Backend Developer
- Purpose: Backend 코드, 오류 처리와 테스트 규칙을 정의합니다.
- Audience: Backend Developer
- Dependencies: `architecture-convention.md`, `../../documents/api/api-response.md`
- Next Reading: `framework-convention.md`

## 명명

- 언어의 표준 명명 규칙을 따릅니다.
- domain 용어는 `../../documents/glossary/glossary.md`와 일치시킵니다.
- 축약어와 범용 이름보다 의도를 드러내는 이름을 사용합니다.

## 코드

- 한 함수와 클래스는 하나의 명확한 책임을 가집니다.
- public 동작의 실패 조건을 명시적으로 처리합니다.
- secret, token, 개인정보와 대용량 body를 로그에 기록하지 않습니다.
- API entity, persistence entity와 domain model의 경계를 의도적으로 관리합니다.

## 오류 처리

- 내부 예외를 외부에 직접 노출하지 않습니다.
- API 오류는 공유 응답 정책과 안정적인 코드에 mapping합니다.
- 예상 가능한 domain 실패와 예기치 않은 system 실패를 구분합니다.

## 테스트

- business rule은 단위 테스트로 검증합니다.
- persistence와 외부 연동은 통합 테스트로 검증합니다.
- API 계약의 성공, validation, 인증, 권한과 not-found 경로를 검증합니다.
- 버그 수정에는 가능한 경우 재현 테스트를 먼저 추가합니다.

## 자동화

- Formatter: `{{FORMATTER_AND_COMMAND}}`
- Linter 또는 static analysis: `{{LINTER_AND_COMMAND}}`
- Test: `{{TEST_COMMAND}}`
