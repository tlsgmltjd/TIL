# apllication.yml-properties, lombok

### application.yml

**YAML 문법**

- Yet Anthoer Markup Language
  - 또 다른 마크업 언어
- 요즘 잘 쓰이는 마크업 언어

```yml
server:
  port: 8080
```

- `key: value` 형태이다.
  > key: server.port / value: 8080  
  > 참/거짓, 숫자, 문자열, 배열(하이픈으로 표햔)

```yml
person:
  student:
  names:
    - 희성
    - 진헌
```

### application.properties

- 중복을 제거하지 않고 키와 벨류를 바로 이어 작성한다.
- 단순하게 나열하여 직관적이다.

```yml
spring.datasource.url=jdbc:...
spring.datasource.username=tlsgmltjd
spring.datasource.password=${DB_PASSWORD}
```

### pofile 적용

- yml에선`---` 로 profile을 구분하여 여러 다른 상황마다 다른 설정을 해줄 수 있다.

```yml
spring:
  config:
    activate:
      on-profile: local

  datasource: ...
---
spring:
  config:
    activate:
      on-profile: dev

  datasource: ...
```

- properties 에선 `apllication-dev.properties` 라는 파일을 새로 만들어서 적용해야한다.

이렇듯 중복이 많고 가독성이 좋지 않아서 properties 방식보다 yml 방식을 더 선호하는 편이다.

### Lombok

- 객체의 getter, setter, 생성자와 같은 중복되는 코드(보일러 플레이트 코드)를 제거할 수 있다.

`@Getter` `@Setter`

- 클래스 위에 붙히면 필드에 대한 getter / setter 가 자동으로 만들어진다.

`@NoArgsConstructor`
`@AllArgsConstructor`
`@RequiredArgsConstructor`

- 기본 생성자 / 모든 필드 / final 필드에 대한 생성자를 자동으로 만들어준다.

> `(access = (access = AccessLevel.PROTECTED))`
> 해당 생성자의 접근 제어자를 설정한다.

`@Builder`

- 생성자에 필요한 데이터만 유연하게 설정할 수 있는 빌더 패턴을 적용시켜주는 어노테이션 이다.

```java
@Builder
publid class Student {
  private String name;
  private Integer age;
  private String schoolName
  private Integer schoolNumber;

  ...
}

...

Student jinheon = Stuent.builder()
  .agr(17)
  .name("jinheon")
  .schoolNumber(1116)
  .build();

```
