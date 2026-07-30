# Git Convention

- Owner: Architect
- Purpose: 변경 이력을 일관되고 검색 가능하게 유지하기 위한 commit 단위와 메시지 규칙을 정의합니다.
- Audience: 모든 역할
- Dependencies: `governance.md`
- Next Reading: `feature-lifecycle.md`

## 원칙

- 하나의 commit은 하나의 설명 가능한 변경 목적만 가집니다.
- commit만 읽어도 무엇이 바뀌었고 왜 필요한지 추적할 수 있어야 합니다.
- 관련 코드, 테스트와 문서 변경은 같은 목적이면 하나의 commit에 포함합니다.
- 서로 독립적으로 되돌려야 하는 변경은 별도 commit으로 분리합니다.
- build 실패, test 실패 또는 미완성 상태를 공유 branch의 영구 이력으로 남기지 않습니다.
- secret, credential, 개인정보와 불필요한 생성 파일을 commit하지 않습니다.

## 메시지 형식

Conventional Commits 형식을 사용합니다.

```text
<type>!: <summary>

<body>

<footer>
```

- `type`은 필수입니다.
- `!`는 호환성을 깨는 변경일 때 사용합니다.
- `summary`는 필수입니다.
- `body`와 `footer`는 필요한 경우에만 작성합니다.

### 언어와 표기

- `type`은 정의된 영문 소문자를 사용합니다.
- `summary`와 `body`는 기본적으로 한국어를 사용합니다.
- 외부 협업 등으로 영어를 사용해야 하면 프로젝트 기준선에서 언어를 변경하고 한 commit 안에서 언어를 혼용하지 않습니다.
- `summary`는 72자 이내로 작성하고 마침표를 붙이지 않습니다.
- `summary`는 파일명 나열보다 변경 결과를 설명합니다.
- `body`는 한 줄을 100자 이내로 유지하는 것을 권장합니다.

## Type

| Type | 사용 기준 |
| --- | --- |
| `feat` | 사용자 또는 외부 소비자가 인지할 수 있는 기능 추가 |
| `fix` | 잘못된 동작이나 결함 수정 |
| `docs` | 문서만 변경 |
| `refact` | 외부 동작 변경 없이 내부 구조 개선 |
| `perf` | 성능 개선 |
| `test` | 테스트 추가 또는 수정 |
| `style` | 동작에 영향을 주지 않는 formatting과 lint 수정 |
| `build` | build tool, dependency와 packaging 변경 |
| `ci` | CI/CD 설정과 자동화 변경 |
| `chore` | 위 유형에 포함되지 않는 유지보수 작업 |
| `revert` | 이전 commit 되돌리기 |

한 변경이 여러 type에 걸치면 변경의 주된 사용자 또는 시스템 영향을 기준으로 선택합니다. 분리 가능한 목적이라면 commit을 나눕니다.

## Summary

좋은 summary는 변경 결과를 구체적으로 설명합니다.

```text
feat: 이메일 인증 로그인 추가
fix: 취소된 주문의 결제 재시도 차단
docs: schema migration 검토 기준 추가
refact: 사용자 상태 소유권을 feature로 이동
```

다음과 같은 모호한 summary는 사용하지 않습니다.

```text
update
fix bug
수정
작업 완료
코드 변경
```

## Body

다음 중 하나라도 필요한 경우 body를 작성합니다.

- summary만으로 변경 이유를 설명하기 어려운 경우
- 대안과 tradeoff를 기록할 필요가 있는 경우
- 데이터 migration, 호환성 또는 운영 영향이 있는 경우
- 의도적으로 변경하지 않은 범위를 설명해야 하는 경우

body는 코드 diff를 반복하지 않고 맥락, 이유와 영향을 설명합니다.

```text
fix: 사용자 이메일 중복 허용 문제 수정

애플리케이션 검증만으로는 동시 요청의 중복 생성을 막을 수 없어
email column에 unique constraint를 추가한다.
```

## Footer

- 관련 작업: `Refs: TASK-123`
- GitHub issue 종료: `Closes: #123`
- 여러 항목 연결: `Refs: TASK-123, TASK-124`
- 호환성을 깨는 변경 설명: `BREAKING CHANGE: <영향과 migration 방법>`

호환성을 깨는 변경은 header의 `!`와 `BREAKING CHANGE:` footer를 함께 사용합니다.

```text
feat!: 사용자 응답에서 legacyName 제거

BREAKING CHANGE: API 소비자는 displayName을 사용해야 한다.
Refs: TASK-123
```

## 특수 Commit

- 저장소의 최초 commit은 `Initial commit`을 예외적으로 허용합니다.
- Merge commit은 Git이 생성한 기본 메시지를 허용합니다.
- Revert는 `revert: <되돌리는 변경>` 형식을 사용하고 대상 commit hash와 이유를 body에 기록합니다.
- 자동 생성 파일은 생성 원본과 같은 commit에 포함합니다.
- schema migration은 이를 사용하는 코드 및 관련 schema 문서와 배포 순서에 맞게 commit합니다.

## Branch와 History

- `WIP`, `temp`, `checkpoint` commit은 개인 branch에서만 일시적으로 허용하며 공유 이력에 반영하기 전에 정리합니다.
- Squash merge를 사용하면 최종 PR 제목 또는 squash commit 메시지가 이 규칙을 따라야 합니다.
- 이미 공유된 commit의 history를 임의로 rewrite하지 않습니다.
- force push가 필요하면 영향받는 기여자와 범위를 확인하고 명시적으로 승인받습니다.

## Commit 전 확인

- [ ] 하나의 변경 목적만 포함합니다.
- [ ] 관련 문서와 테스트를 함께 갱신했습니다.
- [ ] formatter, lint, test와 필요한 build 검증을 통과했습니다.
- [ ] 생성 파일, migration과 source 문서가 일치합니다.
- [ ] secret, 개인정보와 로컬 전용 파일이 포함되지 않았습니다.
- [ ] type과 summary가 실제 변경을 정확히 설명합니다.
- [ ] breaking change, issue와 task 연결이 footer에 기록되어 있습니다.
