# Git History Convention

## 공유 이력

- **STD-COMMON-070** `WIP`, `temp`, `checkpoint` commit은 개인 branch에서만 일시적으로 사용하고 공유 이력에 반영하기 전에 정리합니다.
- **STD-COMMON-071** squash merge를 사용하면 최종 PR 제목 또는 squash commit 메시지도 이 규칙을 따릅니다.
- **STD-COMMON-072** 이미 공유한 commit의 history를 임의로 rewrite하지 않습니다.
- **STD-COMMON-073** force push는 영향 범위와 기여자를 확인하고 명시적인 사용자 승인을 받은 경우에만 수행합니다.
- **STD-COMMON-074** 자동 생성 파일은 생성 원본과 같은 commit에 포함합니다.
