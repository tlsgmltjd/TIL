# HTTP 헤더 개요

> header-field = field-name : OWS field-values OWS (OWS:띄어쓰기허용)

```
HTTP/1.1 200 OK
Content-Type: application/json <- header
```

### 용도

- HTTP 전송에 필요한 모든 부가정보가 들어간다
- 메시지 바디의 내용, 크기, 압축 인증, 캐시 관리 정보 등등등...
- 표준 헤더가 너무 많다
- 필요에 따라 임의의 헤더를 추가할 수 있다.

### HTTP BODY

> HTTP 표준이 RFC261이 폐기되면서 RFC7230 ~ 7235가 등장했다.

- 엔티티 -> 표현
- Representation = representation Metadata + representation Data
- 표현 = 표현 메타데이터 + 표현 데이터

```
HTTP/1.1 200OK
---
Content-Type: text/html
Content-Length: 1000
--- 표현 헤더

---
<html>
...
--- 표현 데이터
```

- **메시지 본문을 통해 표현 데이터를 전달**한다
- 메시지 본문 = 페이로드
- **표현**은 요청이나 응답에서 전달할 실제 데이터이다
- **표현 헤더는 표현 데이터를 해석할 수 있는 정보**를 제공한다
  - 데이터 유형(html, json, text), 데이터 길이, 압축 정보 등등
- 표현 헤더는 표현 메타데이터와, 페이로드 메시지를 구분해야하지만 생략한다

# 표현

- Content-Type: 표현 데이터의 형식
- Content-Encoding: 표현 데이터의 압축 방식
- Content-Language: 표현 데이터의 자연 언어
- Content-Length: 표현 데이터의 길이

* 표현 헤더는 전송, 응답 둘다 사용한다

## Content-Type

> 표현 데이터의 형식 설명

```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 100

{"bookname":"오브젝트}
```

- 미디어 타입, 문자 인코딩
- ex
  - text/html
  - application/json
  - image/png

## Content-Encoding

> 표현 데이터 인코딩

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Encoding: gzip
Content-Length: 100

gdf96hj9fgh97gf659jh876fgsh76fs
```

- 표현 데이터를 압축하기 위해 사용한다
- 데이터를 전달하는 곳에서 압축 후 인코딩 헤더를 추가한다
- 데이터를 읽는 쪽에서 인코딩 헤더를 정보를 통해 압축을 해제한다
- ex
  - gzip
  - deflate
  - identity (압축 안한다)

## Content-Language

> 표현 데이터의 자연 언어

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Language: ko
Content-Length: 100

<html>
안녕하세요
</html>
```

- 표현 데이터의 자연 언어를 표현한다
- ex
  - ko
  - en
  - en-US

## Content-Length

> 표현 데이터의 길이

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Language: en
Content-Length: 2

hi
```

- 바이트 단위

- Transfer-Encoding(전송 코딩)을 사용하면 Content-Length를 사용하면 안됨
  - Transfer-Encoding안에 정보들이 다 들어가 있어서 그렇다
