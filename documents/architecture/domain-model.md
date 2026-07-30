# 도메인 모델

- Owner: Architect
- Purpose: 프로젝트 수준 도메인 개념과 관계를 정의합니다.
- Audience: 모든 역할
- Dependencies: `../glossary/glossary.md`, `../product/business-rule.md`
- Next Reading: `architecture.md`

## Aggregate 및 Entity

### {{DOMAIN_CONCEPT}}

- 유형: Aggregate Root | Entity | Value Object | Domain Service
- 책임: {{RESPONSIBILITY}}
- 식별자: {{IDENTIFIER}}
- 주요 속성: {{KEY_ATTRIBUTES}}
- 생명주기: {{LIFECYCLE}}
- 관련 규칙: `BR-{{NUMBER}}`

## 관계

- {{CONCEPT_A}}는 {{RELATIONSHIP}}을 통해 {{CONCEPT_B}}와 연결됩니다.
- Cardinality: {{CARDINALITY}}
- 소유권: {{OWNER}}

## Invariant

- {{INVARIANT}}

## 경계

- 이 문서는 프로젝트 수준 의미를 정의합니다.
- persistence entity와 Frontend type은 이 모델을 따르되 역할별 구현 세부사항은 각 역할 문서에서 관리합니다.
