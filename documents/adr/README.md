# ADR

## 목적

이 템플릿을 적용한 실제 프로젝트의 장기적인 architectural decision record를 저장합니다.

## 템플릿 상태

- `project-default`에는 이 `README.md`만 유지합니다.
- 템플릿 자체의 변경 이력은 Git commit log에서 관리하며 ADR로 기록하지 않습니다.
- 템플릿에 예시 또는 placeholder ADR 파일을 추가하지 않습니다.
- 실제 프로젝트가 이 템플릿을 적용한 이후 발생한 프로젝트 고유 결정만 이 디렉터리에 기록합니다.
- 프로젝트 초기 ADR 번호는 `001`부터 시작합니다.

## 파일 이름

`NNN-short-title.md` 형식을 사용합니다.

예:

```text
001-database-choice.md
002-authentication-strategy.md
```

## 작성 절차

1. 실제 프로젝트에 장기적인 영향을 주는 결정인지 확인합니다.
2. `../../architect/decision-template.md`를 복사합니다.
3. 맥락, 선택지, tradeoff와 결정을 작성합니다.
4. `../../architect/decision-log.md`에 인덱스를 추가합니다.
5. 영향을 받는 공유 문서와 역할별 문서를 갱신합니다.
