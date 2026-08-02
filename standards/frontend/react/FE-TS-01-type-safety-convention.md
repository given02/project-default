# TypeScript Type Safety Convention

## 기준

- **STD-FE-TS-010** TypeScript strict mode를 사용하며 개별 오류를 반복적으로 비활성화해 우회하지 않습니다.
- **STD-FE-TS-011** `any` 대신 `unknown`, generic 또는 구체적인 type을 사용하고 외부 입력은 runtime에서 좁힙니다.
- **STD-FE-TS-012** nullable은 값이 없을 수 있음을, optional은 property가 생략될 수 있음을 표현하며 둘을 무의미하게 혼용하지 않습니다.
- **STD-FE-TS-013** 제품 상태는 가능한 경우 discriminated union으로 표현해 유효하지 않은 조합을 만들 수 없게 합니다.
- **STD-FE-TS-014** type assertion은 runtime 검증이나 type system이 표현하지 못하는 명확한 근거가 있을 때만 사용합니다.
- **STD-FE-TS-015** non-null assertion으로 실제 nullable 경로를 숨기지 않습니다.
