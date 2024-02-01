# URI

> Uniform Resource Indentifier

URI는 **로케이터**, **이름** 또는 둘다 추가로 분류될 수 있다.

```
URI(Identifier) [URL(Locator) URN(Name)]
```

## URL

- Uniform : 리소스를 식별하는 통일된 방식
- Resource : 자원, URI로 식별할 수 있는 모든것
- Identifier : 다른 항목과 구분하는데 사용하는 정보

## URL / URN

- URL - Locator 리소스가 있는 위치를 지정
- URN - Name 리소르 이름을 부여
- 위치는 변할 수 있지만 이름은 변하지 않음
- URN, 자원의 이름만으로 리소스를 찾는 방법은 보편화 되지 않음

## URL 분석

```
https://(userinfo@)www.google.com:433/search?q=hello&hl=ko
```

### scheme

- 주로 프로토콜(자원을 접근하는 방식) 사용
- ex. http, https, ftp

### userinfo

- URL에 사용자 정보를 포함해서 인증할 때 사용
- 거의 사용 안함

### host

- 호스트명
- 도메인명이나 IP주소

### PORT

- 포트, 생략 가능
- 일반적으로 생략, http: 80, https: 443

### path

- 리소스 경로, 대부분 계층적 구조로 되어있음
- ex. feeds/123

### query

- key=value 형태이다
- ?로 시작하며 &로 추가할 수 있다.
- query parameter, query string으로 불림

### fragment

- fragment
- html 내부 북마크에 사용
- 서버에 전송 안됨
