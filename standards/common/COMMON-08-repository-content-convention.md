# Repository Content Convention

## 추적 대상

- **STD-COMMON-080** source, test, 문서, migration, 재현 가능한 build 설정과 dependency lockfile처럼 프로젝트를 다시 만들고 검증하는 데 필요한 파일을 Git에 추적합니다.
- **STD-COMMON-081** IDE의 개인 설정, 운영체제 파일, local environment, credential, cache, log, 일회성 output과 다시 생성할 수 있는 build 결과는 `.gitignore`로 제외합니다. Codex의 local 임시 상태는 제외하되 `.codex/config.toml`과 `.codex/agents/`의 공유 설정은 유지합니다.
- **STD-COMMON-082** 공유해야 하는 설정 예시는 실제 secret이 없는 `.env.example` 또는 동등한 sample 파일로 제공하고 실제 `.env` 값은 추적하지 않습니다.
- **STD-COMMON-083** 생성된 source나 문서가 소비자의 build 또는 배포에 필요한 경우 생성 원본과 같은 commit에 포함합니다. 임시 생성 결과와 재생성 가능한 산출물은 추적하지 않습니다.

## Ignore와 staging

- **STD-COMMON-084** `.gitignore` 패턴은 용도와 경로가 분명한 대상에만 적용합니다. source, test, migration, 문서, dependency lockfile과 wrapper를 확장자 전체나 상위 폴더 전체로 무시하지 않습니다.
- **STD-COMMON-085** 새 파일을 추가하기 전 `git status --short`와 stage 대상 목록을 확인하고, commit 직전 `git diff --cached --name-status`로 추적할 파일만 포함됐는지 검토합니다.
- **STD-COMMON-086** `.gitignore`는 아직 추적하지 않는 파일에만 적용됩니다. 이미 추적 중인 불필요한 파일은 정확한 경로와 영향 범위를 확인한 뒤 파일의 local 사본을 유지하면서 index에서만 제거합니다.
- **STD-COMMON-087** 필요한 파일이 ignore되는 경우 `git check-ignore -v`로 원인을 확인하고 범위가 좁은 예외 규칙을 추가합니다. `git add -f`를 반복적인 해결책으로 사용하지 않습니다.
- **STD-COMMON-088** project별 새 도구나 생성 경로가 생기면 해당 경로의 필요성과 재생성 방법을 확인해 project `.gitignore`에 구체적인 패턴을 추가합니다.
- **STD-COMMON-089** Agent는 사용자가 요청하지 않은 임시 `output/`, `outputs/`, `tmp/`, `temp/`, `scratch/` 폴더를 만들지 않습니다. 명시적으로 요청한 납품 파일은 추적 여부를 사용자 요구와 산출물의 재생성 가능성에 맞춰 결정합니다.
