# 아키텍처

- Owner: Architect
- Purpose: 프로젝트 수준 시스템 구조와 컴포넌트 경계를 정의합니다.
- Audience: 모든 역할
- Dependencies: `domain-model.md`, `dependency-rule.md`
- Next Reading: `dependency-rule.md`

## 개요

{{SYSTEM_OVERVIEW}}

## 컴포넌트

| 컴포넌트 | 책임 | 소유 데이터 | 외부 인터페이스 |
| --- | --- | --- | --- |
| {{COMPONENT}} | {{RESPONSIBILITY}} | {{OWNED_DATA}} | {{INTERFACE}} |

## 데이터 흐름

1. {{FLOW_STEP}}
2. {{FLOW_STEP}}

## 외부 시스템

| 시스템 | 목적 | 연동 방식 | 장애 시 동작 |
| --- | --- | --- | --- |
| {{EXTERNAL_SYSTEM}} | {{PURPOSE}} | {{PROTOCOL}} | {{FAILURE_BEHAVIOR}} |

## 품질 속성

- 성능: {{PERFORMANCE_APPROACH}}
- 보안: {{SECURITY_APPROACH}}
- 확장성: {{SCALABILITY_APPROACH}}
- 관측 가능성: {{OBSERVABILITY_APPROACH}}

## 아키텍처 결정

- 주요 선택은 `../adr/`와 `../../architect/decision-log.md`에서 관리합니다.
