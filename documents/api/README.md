# API

## 목적

Backend와 Frontend 또는 외부 소비자 사이의 공유 API 계약을 관리합니다.

## 문서

- `api-contract.md`: endpoint, 요청, 응답과 인증 요구사항
- `api-response.md`: 공통 성공 및 실패 응답 정책

## 원칙

- API는 구현 전에 문서화합니다.
- persistence entity를 외부 계약으로 직접 사용하지 않습니다.
- 호환성을 깨는 변경에는 영향 분석과 마이그레이션 계획이 필요합니다.
- OpenAPI 등 기계 판독 가능한 명세를 사용한다면 이 문서와 생성 전략을 명시적으로 정렬합니다.
