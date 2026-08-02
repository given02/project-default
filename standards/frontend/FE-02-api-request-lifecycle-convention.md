# Frontend API Request Lifecycle Convention

## 기준

- **STD-FE-020** 화면 전환, 검색 조건 변경과 component 해제 시 더 이상 필요 없는 요청을 취소하거나 stale 응답을 무시합니다.
- **STD-FE-021** 동일 mutation의 중복 제출을 방지하고 필요한 경우 API의 idempotency 계약을 사용합니다.
- **STD-FE-022** mock과 fixture는 실제 API 계약에서 파생하거나 같은 변경에서 함께 갱신해 분기되지 않게 합니다.
- **STD-FE-023** client bundle에 secret, private credential과 서버 전용 환경 값을 포함하지 않습니다.
