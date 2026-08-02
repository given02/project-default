# React Routing Convention

## 기준

- **STD-FE-REACT-050** route path와 parameter 정의는 하나의 route 구성 경계에서 관리합니다.
- **STD-FE-REACT-051** page component는 route parameter를 해석하고 feature를 조합하되 API 및 비즈니스 로직을 직접 소유하지 않습니다.
- **STD-FE-REACT-052** client guard는 사용자 흐름을 제어할 뿐 서버의 인증과 인가를 대체하지 않습니다.
- **STD-FE-REACT-053** unknown path, route loading, navigation failure와 권한 부족 상태를 명시적으로 처리합니다.
- **STD-FE-REACT-054** 외부 입력인 path와 query parameter는 사용 전에 parse하고 유효하지 않은 값의 fallback을 정의합니다.
