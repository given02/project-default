# Python Format Convention

## 기본 형식

- **STD-BE-PY-010** 모든 Python source와 type stub은 루트 `.editorconfig`와 `ruff.toml`의 UTF-8, LF, final newline, trailing whitespace 제거, space 4칸 들여쓰기와 100자 line width 기준을 적용합니다.
- **STD-BE-PY-011** tab 문자로 들여쓰지 않고 하나의 logical indentation level에 space 4칸을 사용합니다. semicolon으로 여러 statement를 한 줄에 나열하지 않습니다.
- **STD-BE-PY-012** string은 Ruff의 double quote 형식을 따르고 module·class·function 사이의 빈 줄, 연산자와 comma 공백을 수동 정렬하지 않고 formatter 결과에 맡깁니다.

## 줄바꿈과 import

- **STD-BE-PY-013** function 선언, 호출 인자, collection, comprehension과 복합 표현식이 100자 기준을 넘으면 괄호 안의 문법 경계에서 여러 줄로 나누고 multiline item에는 trailing comma를 사용합니다.
- **STD-BE-PY-014** 명시적인 backslash로 줄을 이어 붙이지 않고 parentheses, brackets 또는 braces의 implicit line joining을 사용합니다. formatter를 피하기 위한 과도한 축약이나 중첩 표현식을 사용하지 않습니다.
- **STD-BE-PY-015** import는 standard library, third-party와 first-party group으로 정렬하고 wildcard import와 사용하지 않는 import를 남기지 않습니다. import 순서는 수동으로 관리하지 않고 Ruff `I` 규칙으로 검증합니다.

## 자동화와 IDE

- **STD-BE-PY-016** 프로젝트 개발 dependency에 Ruff version을 명시적으로 고정하고 루트 `ruff.toml`을 formatter와 lint의 source of truth로 사용합니다. line length 100, indent width 4, `E501`, import 정리, double quote, LF와 docstring code format을 활성화합니다.
- **STD-BE-PY-017** local 자동 수정은 `ruff check --fix` 후 `ruff format` 순서로 실행하고, 검증은 `ruff check`와 `ruff format --check`로 실행합니다. 두 검증을 CI와 프로젝트의 표준 test 또는 check entrypoint에 포함하며 실패 상태로 Review 전환이나 commit을 완료하지 않습니다.
- **STD-BE-PY-018** IntelliJ와 PyCharm은 repository `.editorconfig`와 project Ruff configuration을 사용합니다. IDE 자체 reformat 결과와 Ruff가 다르면 version이 고정된 Ruff 결과를 source of truth로 사용합니다.
- **STD-BE-PY-019** Agent가 생성하거나 수정해 repository에 commit하는 Python source도 같은 Ruff 검증을 적용합니다. build 과정에서 생성되어 commit하지 않는 source는 검사 대상에서 제외할 수 있지만 생성 결과를 production source처럼 관리하면 제외하지 않습니다.

