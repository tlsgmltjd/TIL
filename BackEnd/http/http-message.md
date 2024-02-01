# HTTP 메시지

## HTTP 메시지 구조

```
[start-line] 시작라인
[header] 헤더
[empty-line] 공백 라인 (CRLF)
[message-body]
```

```
GET /member?name=shs HTTP/1.1
Host: www.oneus.com

```

> ex. HTTP 요청 메시지

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1000

<html>...
```

> ex. HTTP 응답 메시지

---

## 시작 라인 (요청 메시지)

- start-line = request-line

- method SP(공백) request-target SP HTTP-version CRLF(엔터)

### method

종류 : GET POST PUT DELETE...
서버가 수행해야할 동작을 지정한다.

### request-target

- absolute-path[?query] 절대경로?쿼리
- 절대경로 = / 로 시작하는 경로

### HTTP-version

## 시작 라인 (응답 메시지)

- start-line

- HTTP-version SP status-code SP reason-phrase CRLF

## HTTP 헤더

- header-field = field-name: OWS field-value OWS (OWS: 띄어쓰기 허용)
- field-name은 대소문자 구분 없음

### 용도

- HTTP 전송에 필요한 모든 메타데이터가 있다.

- 메시지 바디의 내용, 크키, 압축, 인증, 요청 클라이언트, 서버 애플레케이션, 캐시 관련 정보.......

- 표준 헤더가 너무 많다.
- 임의의 헤더 추가 가능

## HTTP 메시지 바디

- 실제 전송할 데이터
- HTML, 이미지, 영상, JSON... byte로 표현 가능한 모든 데이터

---

## HTTP 정리

- HTTP 메시지에 모든 것을 전송할 수 있다
- HTTP/1.1 기준으로 공부하면 된다
- 클라이언트 / 서버 구조이다.
- 무상태 프로토콜이다.
- 비연결성을 지향한다.
- HTTP 메시지로 요청과 응답이 오간다.
- 단순하고 확장이 가능하다

* 지금은 HTTP 시대이다
