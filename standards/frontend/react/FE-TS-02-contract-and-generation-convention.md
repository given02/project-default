# TypeScript Contract And Generation Convention

## 기준

- **STD-FE-TS-020** API type은 Customs 계약 또는 선택한 생성 원본과 일치시키고 화면 편의를 위해 응답 type을 조용히 변경하지 않습니다.
- **STD-FE-TS-021** 생성된 type과 client 파일은 직접 수정하지 않고 생성 원본과 명령을 변경합니다.
- **STD-FE-TS-022** `enum`, string union과 상수 object 중 선택은 serialization, runtime 접근과 확장 필요성을 기준으로 일관되게 사용합니다.
- **STD-FE-TS-023** public component, Hook와 API 함수의 입출력에는 추론 결과가 불명확해지지 않도록 명시적인 type 경계를 둡니다.
- **STD-FE-TS-024** `@ts-ignore`는 사용하지 않으며 불가피한 억제는 오류 코드와 근거를 포함한 `@ts-expect-error`로 제한합니다.
