# 클라이언트에서 서버로 데이터 전송

**쿼리 파라미터**로 데이터 전송

- GET
- 주로 정렬 필터 검색어

**메시지 바디**를 통한 데이터 전송

- POST, PUT, PATCH
- 회원가입, 상품주문, 리스트등록, 리소스변경

### 1. 정적 데이터 조회

> 쿼리 파라미터 미사용

- 이미지, 정적 텍스트 문서
- 조회는 GET 사용
- 정적 데이터는 일반적으로 쿼리 파라미터 없이 리소스 URL로 단순하게 조회 가능

### 2. 동적 데이터 조회

> 쿼리 파아미터 사용

```
GET /search?q=asdf HTTP/1.1
Host: www.google.com
```

-> [GET]

서버에서 메시지를 해석하여 쿼리 파라미터를 기반으로 결과 데이터를 동적으로 생성한다.

- 주로 검색, 정렬 필터에서 사용
- 조회 조건을 줄여주는 필터, 정렬하는 정렬 조건에서 사용
- 조회는 GET
- GET은 쿼리 파라미터를 사용해서 데이터 전달

### 3. HTML Form 데이터 전송

> **POST 전송 - 저장**

```html
<form action="/book" method="post">
  <input type="text" name="bookname" />
</form>
```

> 전송시 웹 브라우저가 폼 데이터를 읽어서 HTTP 메시지를 생성해준다.

```
POST /book HTTP/1.1
Host: locahost:8080
Content-Type: application/x-www-form-urlencoded

bookname=오브젝트
```

action=GET으로 데이터를 넘긴다면?

```html
<form action="/book" method="get">
  <input type="text" name="bookname" />
</form>
```

```
GET /book?bookname=오브젝트 HTTP/1.1
Host: locahost:8080
```

> GET은 조회에만 사용한다. 쿼리 파리미터에 데이터를 넣어 HTTP 메시지를 사용한다.

> 리소스를 바꾸거나 변경하는 작업에는 GET 메서드를 사용하면 안된다!!

> **multipart/form-data**

```html
<form action="/book" method="get">
  <input type="text" name="bookname" />
  <input type="file" name="cover" />
</form>
```

> 웹 브라우저가 생성해준 HTTP 메시지

```
POST /book HTTP/1.1
Host: locahost:8080
Content-Type: multipart/form-data; boundary=---XXX

------XXX
Content-Disposition: form-data; name="bookname"

오브젝트

------XXX
Content-Disposition: form-data; name="cover" filename="book_1.png"
Content-Type: image/png

12ge87d9383y89fhiof023hf023hefi08h2...
------XXX
```

---

### HTML Form 데이터 전송 정리

- HTML Form submit시 POST 전송
  - ex. 회원가입, 글 작성, 리소스 변경
- Content-Type: application/x-www-form-urlencoded 사용
  - form의 내용을 메시지 바디를 통해 전송한다 key = value 형식임
  - 전송 데이터를 url encoding 처리
    - ex. gg김 -> gg%EA%B9%80
- HTML Form은 GET 전송도 가능
- Content-Type: multipart/form-data
  - 파일 업로드 같은 바이너리 데이터 전송시 사용한다.
  - 다른 종류의 여러 파일과 폼의 내용을 함께 전송할 수 있다.
- HTML Form 전송은 **GET, POST만 지원한다.**

---

### 4. HTTP API 데이터 전송

```
POST /book HTTP/1.1
Host: locahost:8080
Content-Type: application/json

{
    "bookname" : "오브젝트",
    "price" : 10000
}
```

- 서버 to 서버
  - 백엔드 시스템 통신
- 앱 클라이언트
  - 아이폰, 안드로이드
- 웹 클라이언트
  - HTML애서 Form 전송 대신 JS를 통한 통신에 사용
  - React, Vue 같은 웹 클리이언트와 API 통신
- POST, PUT, PATCH: 메시지 비디를 통해 데이터 전송
- GET: 조회, 쿼리파라미터로 데이터 전송
- Content-Type: application/json을 주로 사용한다 (표준)
  - TEXT, XML, JSON 등등..
