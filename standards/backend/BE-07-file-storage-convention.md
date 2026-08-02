# File Storage Convention

이 문서는 Customs에서 파일 저장 기능을 선택한 경우에 적용합니다.

## 기준

- **STD-BE-070** storage provider, 허용 형식, 최대 크기, 공개 범위와 보존 정책은 Customs에 명시합니다.
- **STD-BE-071** client가 제공한 파일명이나 경로를 object key 또는 filesystem path로 직접 사용하지 않습니다.
- **STD-BE-072** 파일 확장자와 client의 content type만 신뢰하지 않고 실제 content와 허용 정책을 검증합니다.
- **STD-BE-073** private file의 업로드, 조회, 교체와 삭제마다 서버 측 권한을 검증합니다.
- **STD-BE-074** storage credential과 서명 비밀을 코드, 문서와 client에 노출하지 않습니다.
- **STD-BE-075** Database metadata와 object 저장이 분리되면 부분 실패, 재시도, 고아 파일 정리와 idempotency 전략을 정의합니다.
- **STD-BE-076** 파일 교체와 삭제는 보존, 복구, 연관 데이터와 개인정보 삭제 정책을 따릅니다.
- **STD-BE-077** 원본 파일명은 표시용 metadata로만 다루고 header와 다운로드 파일명에 사용할 때 안전하게 정규화합니다.
- **STD-BE-078** 사용자 제공 파일을 실행 가능한 경로에 저장하거나 서버가 임의 실행·해석하지 않습니다.
