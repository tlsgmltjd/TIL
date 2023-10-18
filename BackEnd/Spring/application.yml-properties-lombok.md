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
