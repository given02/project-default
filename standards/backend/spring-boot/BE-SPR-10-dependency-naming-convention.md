# Spring Boot Dependency Naming Convention

## 생성자 주입 의존성 이름

- **STD-BE-SPR-100** Spring component의 생성자 주입 대상 `final` field와 생성자 매개변수는 선언 타입의 단순 이름을 `lowerCamelCase`로 변환해 이름을 짓습니다. 타입의 책임을 숨기는 짧은 별칭을 사용하지 않습니다. 동일 타입의 bean을 여러 개 주입해 이름만으로 구분할 수 없으면 타입 이름에 역할을 나타내는 접미어를 붙이고 기존 bean 선택 방식을 유지합니다.

```java
@RequiredArgsConstructor
class PlacesRepositoryAdapter implements PlacesRepositoryPort {
    private final PlacesJpaRepository placesJpaRepository;
}

@RequiredArgsConstructor
class PlacesService {
    private final PlacesRepositoryPort placesRepositoryPort;
}
```

`PlacesJpaRepository places`처럼 타입을 숨기는 별칭은 사용하지 않습니다. Application service는 이 명명 규칙 때문에 JPA 구현 타입에 직접 의존하지 않으며, 선언한 port의 이름을 따릅니다. 생성자를 직접 작성해야 하는 경우에도 field와 매개변수에 같은 이름을 사용합니다.
