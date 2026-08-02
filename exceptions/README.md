# Exceptions

## 목적

`exceptions/`는 현재 프로젝트에서 Standard 규칙과 다르게 적용할 내용을 관리합니다.

Exception 파일이 존재하면 해당 파일에 선언된 범위에서 예외가 적용됩니다. 제안, 검토 중이거나 더 이상 적용하지 않는 예외는 이 디렉터리에 유지하지 않습니다.

대상 규칙은 [Standards](../standards/README.md)의 규칙 ID로 지정합니다. 작성 책임과 변경 권한은 [AGENTS.md](../AGENTS.md)를 따르며, 구현할 때는 관련 [Task](../tasks/README.md)에 Exception ID를 연결합니다.

## 작성 조건

다음 조건을 모두 만족할 때 Exception을 작성합니다.

- 적용되는 Standard 규칙을 식별할 수 있습니다.
- 프로젝트 요구를 충족하려면 해당 규칙을 그대로 적용할 수 없습니다.
- Standard를 유지할 수 있는 다른 방법을 검토했습니다.
- 예외의 적용 범위를 명확하게 제한할 수 있습니다.
- 대신 적용할 규칙과 검증 방법을 정의할 수 있습니다.
- 위험과 완화 방법을 설명할 수 있습니다.

다음 경우에는 Exception을 작성하지 않습니다.

- Standard가 다루지 않는 프로젝트 고유 정보를 정의하는 경우
- 조건부 Standard에 명시된 기술을 사용하지 않는 경우
- 요구사항이나 설계가 아직 확정되지 않은 경우
- Standard의 의미를 이해하지 못했거나 문서가 서로 충돌하는 경우
- 단순한 구현 편의만을 위해 규칙을 생략하는 경우

## 파일 이름

Exception 파일은 다음 형식을 사용합니다.

```text
exc-<3자리 번호>-<영문 이름>.md
```

예:

```text
exc-001-order-export-native-query.md
exc-002-legacy-auth-token-storage.md
```

- 번호는 `001`부터 순차 증가합니다.
- 파일 이름은 lowercase kebab-case를 사용합니다.
- 제거된 Exception 번호를 다른 의미로 재사용하지 않습니다.
- 제목이나 파일 이름이 바뀌어도 같은 Exception은 기존 번호를 유지합니다.
- 하나의 파일은 하나의 명확한 예외 목적만 소유합니다.

## Exception ID

Exception ID는 다음 형식을 사용합니다.

```text
EXC-001
```

파일 `exc-001-*`와 ID `EXC-001`의 번호는 일치해야 합니다.

다른 문서는 파일 경로 대신 Exception ID를 사용해 예외를 참조합니다.

## 대상 규칙

모든 Exception은 다르게 적용할 Standard 규칙 ID를 하나 이상 명시합니다.

예:

```text
STD-BE-JPA-044
STD-DB-PG-038
```

- 문서 제목이나 파일 경로만으로 대상 규칙을 표현하지 않습니다.
- 대상 Standard 내용을 복사하지 않고 규칙 ID를 참조합니다.
- 여러 규칙을 다르게 적용하면 각 규칙과 Exception의 관계를 설명합니다.
- 대상 규칙을 식별할 수 없으면 Exception을 작성하지 않습니다.

## 적용 범위

Exception은 적용 범위를 구체적으로 제한해야 합니다.

필요한 항목을 조합해 범위를 정의합니다.

- Backend 또는 Frontend
- component 또는 package
- Requirement ID
- Business Rule ID
- API ID
- Screen ID
- Task ID
- 실행 환경

`전체 프로젝트`, `모든 코드`, `필요한 곳`처럼 검증할 수 없는 범위는 사용하지 않습니다.

선언된 범위 밖에서는 원래 Standard가 그대로 적용됩니다.

## 필수 내용

각 Exception 파일은 다음 형식을 사용합니다.

```markdown
# EXC-001: 예외 제목

## 대상 규칙

- `STD-영역-번호`

## 적용 범위

예외가 적용되는 component, 기능, ID와 환경

## 맥락

현재 프로젝트 요구와 Standard를 그대로 적용할 수 없는 상황

## 이유

예외가 필요한 구체적인 근거

## 검토한 대안

Standard를 유지하기 위해 검토한 방법과 사용하지 않은 이유

## 대체 규칙

적용 범위 안에서 원래 Standard 대신 따라야 하는 검증 가능한 규칙

## 위험과 완화

- 위험:
- 완화:

## 검증

예외 구현이 프로젝트 요구와 대체 규칙을 만족하는지 확인하는 방법

## 관련 항목

- Customs ID:
- Task ID:
```

적용되지 않는 선택 항목에는 `해당 없음`과 이유를 기록합니다.

## 효력

- 디렉터리에 존재하는 모든 Exception 파일은 현재 적용 중입니다.
- Exception은 선언된 대상 규칙과 적용 범위만 다르게 적용합니다.
- 명시하지 않은 Standard 규칙은 그대로 적용됩니다.
- 대체 규칙은 구현과 테스트로 검증할 수 있어야 합니다.
- Exception은 제품 요구사항, 비즈니스 규칙, API 또는 데이터 의미를 새로 정의하지 않습니다.
- 구현 범위가 Exception 범위를 넘어가면 별도 Exception이 필요합니다.

## 변경과 제거

- 적용 중인 예외 내용이 바뀌면 기존 파일을 갱신합니다.
- 적용 범위가 달라지거나 목적이 분리되면 새 Exception 파일을 작성합니다.
- 더 이상 적용하지 않는 Exception 파일은 제거합니다.
- 제거된 파일과 변경 이력은 Git history에서 확인합니다.
- 제거된 Exception ID는 다시 사용하지 않습니다.

## 확인 방법

현재 적용 중인 Exception은 이 디렉터리의 `exc-*.md` 파일 목록으로 확인합니다. 별도의 상태나 인덱스를 관리하지 않습니다.
