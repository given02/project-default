# React Rendering Performance Convention

## 기준

- **STD-FE-REACT-030** 측정 없이 광범위한 memoization을 추가하지 않습니다.
- **STD-FE-REACT-031** 큰 목록, 이미지와 무거운 component는 실제 병목을 측정한 뒤 virtualization, 분할 또는 지연 로딩을 적용합니다.
- **STD-FE-REACT-032** Error Boundary를 복구 가능한 UI 경계에 배치하되 API 오류와 validation 오류의 일반 처리 수단으로 사용하지 않습니다.
