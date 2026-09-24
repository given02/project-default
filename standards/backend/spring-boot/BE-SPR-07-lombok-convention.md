# Spring Boot Lombok Convention

## 적용과 의존성

- **STD-BE-SPR-070** Java 기반 Spring Boot 프로젝트는 반복 코드를 줄이기 위해 Lombok을 기본으로 사용하며, build tool에 Lombok version과 annotation processor를 명시합니다.
- **STD-BE-SPR-071** Spring component의 의존성은 `final` field와 `@RequiredArgsConstructor`로 constructor injection하고, 의존성 주입만을 위한 수동 constructor를 작성하지 않습니다.

## 권장 사용

- **STD-BE-SPR-072** 단순 접근자가 필요한 type은 `@Getter`를 사용하고, 변경이 필요한 field에만 제한적으로 `@Setter`를 적용합니다. 모든 field를 변경할 필요가 없는 type에 class 단위 `@Setter`를 적용하지 않습니다.
- **STD-BE-SPR-073** logging field는 `@Slf4j`로 생성하며 로그 내용은 Backend logging과 security 규칙을 따릅니다.
- **STD-BE-SPR-074** 단순한 immutable data carrier에는 `@Value` 또는 Java `record`를 사용하고, mutable data carrier에서 모든 field의 getter, setter, equality와 `toString`이 실제 계약일 때만 `@Data`를 사용합니다.
- **STD-BE-SPR-075** `@Builder`는 유효하지 않은 객체를 만들 수 없도록 validation을 수행하는 constructor 또는 static factory에 적용합니다. domain object와 JPA entity에 class 단위 `@Builder`를 적용해 생성 규칙을 우회하지 않습니다.

## Domain과 JPA 안전성

- **STD-BE-SPR-076** domain object와 JPA entity에는 class 단위 `@Data`와 `@Setter`를 사용하지 않고, 상태 변경은 의미가 드러나는 domain method로 제한합니다.
- **STD-BE-SPR-077** JPA entity의 기본 생성자는 `@NoArgsConstructor(access = AccessLevel.PROTECTED)`로 생성합니다. `force = true`로 불변식과 null 제약을 우회하지 않습니다.
- **STD-BE-SPR-078** JPA entity의 `equals`, `hashCode`와 `toString`은 연관관계, lazy loading과 mutable field를 자동 포함하지 않습니다. Lombok을 사용할 때는 `onlyExplicitlyIncluded = true`와 명시적인 include를 사용하거나 해당 method를 직접 구현합니다.

## 금지와 검증

- **STD-BE-SPR-079** checked exception 책임을 숨기는 `@SneakyThrows`와 Java 문법과 중복되는 Lombok `val`·`var`를 사용하지 않습니다. 루트 `lombok.config`에서 이를 error로 검증하고, Lombok이 생성한 코드의 확인이 필요할 때는 IDE 추측이 아니라 build compile 또는 delombok 결과를 기준으로 합니다.

