# Git Convention

## Commit 단위

- **STD-COMMON-060** 하나의 commit은 하나의 설명 가능한 변경 목적만 가집니다.
- **STD-COMMON-061** 같은 목적의 코드, 테스트, 문서와 migration은 함께 commit합니다.
- **STD-COMMON-062** 독립적으로 되돌려야 하는 변경은 별도 commit으로 분리합니다.
- **STD-COMMON-063** build 또는 test가 실패하는 미완성 상태를 공유 branch의 영구 이력으로 남기지 않습니다.
- **STD-COMMON-064** secret, credential, 개인정보와 불필요한 생성 파일을 commit하지 않습니다.

## 메시지

Conventional Commits 형식을 사용합니다.

```text
<type>!: <summary>

<body>

<footer>
```

- **STD-COMMON-065** `type`과 `summary`는 필수이며 `body`와 `footer`는 필요한 경우에만 작성합니다.
- **STD-COMMON-066** `type`은 영문 소문자, `summary`와 `body`는 한국어를 기본으로 사용하고 한 commit 안에서 언어를 혼용하지 않습니다.
- **STD-COMMON-067** `summary`는 72자 이내로 작성하고 마침표를 붙이지 않으며 파일명보다 변경 결과를 설명합니다.
- **STD-COMMON-068** 변경 이유, trade-off, migration, 호환성 또는 운영 영향이 summary만으로 드러나지 않으면 body에 기록합니다.
- **STD-COMMON-069** 호환성을 깨는 변경은 header의 `!`와 `BREAKING CHANGE:` footer를 함께 사용합니다.

| Type     | 사용 기준                                  |
| -------- | ------------------------------------------ |
| `feat`   | 사용자 또는 외부 소비자가 인지할 기능 추가 |
| `fix`    | 잘못된 동작이나 결함 수정                  |
| `docs`   | 문서만 변경                                |
| `refact` | 외부 동작 변경 없는 내부 구조 개선         |
| `perf`   | 성능 개선                                  |
| `test`   | 테스트 추가 또는 수정                      |
| `style`  | 동작에 영향 없는 formatting과 lint 수정    |
| `build`  | build tool, dependency와 packaging 변경    |
| `ci`     | CI/CD 설정과 자동화 변경                   |
| `chore`  | 다른 유형에 포함되지 않는 유지보수         |
| `revert` | 이전 commit 되돌리기                       |

관련 Task는 `Refs: TSK-001` 형식으로 연결합니다. GitHub issue를 종료할 때는 `Closes: #123`을 사용합니다.
