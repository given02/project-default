# 기능 생명주기

- Owner: Architect
- Purpose: 아이디어부터 릴리스까지의 기능 흐름을 정의합니다.
- Audience: 모든 역할
- Dependencies: `governance.md`, `../documents/product/requirements.md`
- Next Reading: `roadmap.md`

| 단계 | 소유자 | 필수 산출물 | 완료 기준 |
| --- | --- | --- | --- |
| 아이디어 | Architect | 백로그 후보 | 제품 방향과 사용자 가치에 부합 |
| 요구사항 | Architect | 요구사항과 acceptance criteria | 범위와 제외 범위가 명확 |
| 비즈니스 규칙 | Architect | 검증 가능한 규칙 | 중복과 모호함이 없음 |
| 도메인 모델 | Architect | 개념, 관계, 소유권 | 표준 용어와 일치 |
| 아키텍처 검토 | Architect | 경계, 의존성, 필요 시 ADR | 선택과 tradeoff가 기록됨 |
| API 계약 | Architect | 요청, 응답, 오류 계약 | 양쪽 구현이 추측 없이 가능 |
| Backend 구현 | Backend Developer | 코드와 테스트 | 공유 계약과 Backend 규칙 준수 |
| Frontend 구현 | Frontend Developer | 코드와 테스트 | 공유 계약과 Frontend 규칙 준수 |
| 통합 검토 | Architect | 통합 검토 결과 | end-to-end 동작과 문서 일치 |
| 릴리스 | Architect | 릴리스 결정 | 필수 검증과 문서 갱신 완료 |
