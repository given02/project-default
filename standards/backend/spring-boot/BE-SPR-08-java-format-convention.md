# Spring Boot Java Format Convention

## 기본 형식

- **STD-BE-SPR-080** 모든 Java source는 루트 `.editorconfig`의 UTF-8, LF, final newline, trailing whitespace 제거, space 4칸 들여쓰기와 100자 line width 기준을 적용합니다.
- **STD-BE-SPR-081** tab 문자로 들여쓰지 않고 block과 continuation indentation을 space 4칸 단위로 표현합니다. 여러 선언이나 statement를 한 줄에 나열하지 않습니다.
- **STD-BE-SPR-082** 여는 중괄호는 선언 또는 제어문의 같은 줄에 두고, 닫는 중괄호는 대응하는 block indentation에 둡니다. 연산자 양쪽과 comma 뒤에는 공백을 두며 수동 공백으로 여러 줄의 열을 맞추지 않습니다.

## 줄바꿈과 import

- **STD-BE-SPR-083** method 선언, 호출 인자, fluent chain, lambda와 복합 표현식이 formatter 기준을 넘으면 문법 경계에서 여러 줄로 나눕니다. 긴 코드를 한 줄에 유지하기 위한 축약, 가독성이 낮은 중첩 표현식 또는 formatter 비활성화를 사용하지 않습니다.
- **STD-BE-SPR-084** wildcard import를 사용하지 않고 사용하지 않는 import를 제거합니다. static import는 테스트 assertion처럼 출처가 명확하고 가독성을 높이는 경우에만 사용합니다.
- **STD-BE-SPR-085** URL, 오류 원문 또는 분리할 수 없는 literal처럼 formatter가 안전하게 나눌 수 없는 값을 제외하고 100자 기준을 지킵니다. 예외적인 긴 값 때문에 주변 선언과 호출까지 한 줄로 유지하지 않습니다.

## 자동화와 IntelliJ

- **STD-BE-SPR-086** build tool에 Spotless와 `google-java-format`을 명시적인 version으로 고정하고 Java source에 `google-java-format`, long string reflow, unused import 제거와 wildcard import 금지를 적용합니다.
- **STD-BE-SPR-087** local 수정과 검증은 Spotless의 apply와 check entrypoint로 통일합니다. Gradle은 `spotlessApply`와 `spotlessCheck`, Maven은 `spotless:apply`와 `spotless:check`를 사용하고 표준 `check` 또는 `verify` lifecycle이 format 검증을 실행하게 합니다. formatter 검증 실패 상태로 Review 전환이나 commit을 완료하지 않습니다.
- **STD-BE-SPR-088** IntelliJ는 repository `.editorconfig`를 사용하고 저장 또는 commit 전에 build의 formatter를 실행하도록 설정합니다. IntelliJ 자체 reformat 결과와 build formatter가 다르면 version이 고정된 build formatter 결과를 source of truth로 사용합니다.
- **STD-BE-SPR-089** Agent가 생성하거나 수정해 repository에 commit하는 Java source도 같은 formatter를 적용합니다. build 과정에서 생성되어 commit하지 않는 source directory는 검사 대상에서 제외할 수 있지만, 생성 결과를 수동으로 수정하거나 production source처럼 관리하면 제외하지 않습니다.
