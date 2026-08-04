# Database Constraint And Index Convention

## Key와 Constraint

- **STD-DB-030** 모든 table은 명시적인 primary key 또는 Requirement의 Database 설계에 정의된 대체 식별 전략을 가집니다.
- **STD-DB-031** business invariant는 가능한 경우 not-null, unique, foreign key와 check constraint로 Database에서도 보호합니다.
- **STD-DB-032** 모든 foreign key의 delete 및 update 동작을 명시적으로 결정합니다.
- **STD-DB-033** cascade는 데이터 소유권과 생명주기가 같은 경우에만 사용합니다.
- **STD-DB-034** application validation만으로 데이터 무결성을 보장하지 않습니다.

## Index

- **STD-DB-035** index는 실제 query의 filter, join, sort, cardinality와 운영 목적을 근거로 추가합니다.
- **STD-DB-036** foreign key라는 이유만으로 index를 추가하지 않고 참조 방향의 조회와 삭제 비용을 검토합니다.
- **STD-DB-037** 복합 index는 선두 column, 정렬 방향과 조회 조건을 근거로 설계합니다.
- **STD-DB-038** unique constraint가 제공하는 index와 동일한 일반 index를 중복 생성하지 않습니다.
- **STD-DB-039** 낮은 cardinality의 단일 column index와 쓰기 비용이 큰 index는 대표 데이터에서 효과를 검증합니다.
