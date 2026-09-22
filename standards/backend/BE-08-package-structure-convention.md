# Backend Package Structure Convention

## 기본 구조

- **STD-BE-080** Backend package는 기술 계층을 전체 application 단위로 먼저 나누지 않고 `user`, `order`처럼 Requirement에서 정의한 business domain을 먼저 나눈 뒤 각 domain 내부를 책임별로 구성합니다.
- **STD-BE-081** Spring Boot application 진입점은 모든 domain package의 공통 상위 base package에 둡니다. 예를 들어 `com.jhome.core.CoreApplication` 아래에 `user`와 `order` domain package를 둡니다.
- **STD-BE-082** 독립 배포되는 단일 domain service는 base package가 이미 domain을 나타내면 domain package를 한 번 더 만들지 않으며, 역할이 없는 빈 package도 형식적으로 생성하지 않습니다.

```text
com.jhome.core
├── CoreApplication.java
├── user
│   ├── api
│   ├── application
│   ├── domain
│   └── infrastructure
└── order
    ├── api
    ├── application
    ├── domain
    └── infrastructure
```

## Package 책임

- **STD-BE-083** `api`에는 Controller, 외부 request·response model, 입력 형식 검증과 protocol 변환을 두며 repository, persistence model과 business rule을 직접 사용하지 않습니다.
- **STD-BE-084** `application`에는 use case service, command·query·result model, transaction boundary와 외부 기능에 요구하는 port를 두고 domain 동작과 port 호출 순서를 조정합니다.
- **STD-BE-085** Application service는 구체적인 adapter, Spring Data repository, QueryDSL과 persistence entity가 아니라 application이 소유한 port에 의존합니다.
- **STD-BE-086** `domain`에는 entity, aggregate, value object, policy, domain event와 domain failure를 두며 Spring MVC, Spring Data, JPA, QueryDSL, HTTP와 database vendor 타입에 의존하지 않습니다.
- **STD-BE-087** `infrastructure`에는 application port를 구현하는 adapter, persistence entity, framework repository, external client와 messaging 구현을 두며 JPA와 QueryDSL은 adapter 내부 구현으로만 사용합니다.

## Port와 복잡성 관리

- **STD-BE-088** Application port는 domain 또는 application model과 기술 독립 타입으로 계약을 표현합니다. Aggregate 저장·조회는 repository port가 소유하고 복잡한 목록·검색·통계가 독립적으로 필요할 때만 query port를 분리하며 framework paging, query와 persistence 타입을 노출하지 않습니다.
- **STD-BE-089** `infrastructure`는 기본적으로 domain 내부에 평평하게 유지하고 persistence, cache, client 또는 messaging처럼 서로 다른 책임의 구현이 실제로 늘어나 탐색이 어려울 때만 책임 기준 하위 package로 나눕니다. JPA, QueryDSL 또는 PostgreSQL을 사용한다는 이유만으로 기술별 package를 만들지 않습니다.

기본적인 JPA와 QueryDSL 구성은 다음처럼 기술 package를 추가하지 않고 표현할 수 있습니다.

```text
user
├── api
│   ├── UserController.java
│   ├── AddUserRequest.java
│   └── UserResponse.java
├── application
│   ├── AddUserService.java
│   ├── AddUserCommand.java
│   ├── AddUserResult.java
│   └── port
│       ├── UserRepositoryPort.java
│       └── UserQueryPort.java
├── domain
│   ├── User.java
│   └── InvalidUserException.java
└── infrastructure
    ├── UserJpaEntity.java
    ├── UserJpaRepository.java
    ├── UserRepositoryAdapter.java
    └── UserQueryAdapter.java
```

`UserRepositoryAdapter`는 `UserRepositoryPort`를 구현하고 내부에서 `UserJpaRepository`를 사용합니다. `UserQueryAdapter`는 복잡한 조회가 실제로 있을 때만 `UserQueryPort`를 구현하고 QueryDSL을 내부에서 사용할 수 있습니다. 변환이 한 adapter에만 있고 단순하면 private 변환으로 시작하며, 복잡하거나 재사용될 때 persistence mapper를 분리합니다.
