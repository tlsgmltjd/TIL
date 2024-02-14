# 3xx 리다이렉션 Redirection

> 요청을 완료하기 위해 유저 에이전트(웹 브라우저)의 추가 조치 필요

- 300 Multiple Choices
- 301 Moved Permanently
- 302 Found
- 303 See Other
- 304 Not Modified
- 307 Temporary Redirect
- 308 Permanent Redirect

### 리다이렉션

- 웹 브라우저는 300대 응답 결과에 Location 헤더가 있으면 자동으로 Location 경로로 이동한다.

#### 종류

- 영구 리다이렉션 - 특정 리소스의 URI가 영구적으로 이동
  - ex. /books -> /lib
- 일시 리다이렉션 - 일시적인 변경
  - 주문 완료 후 주문 내역 화면으로 이동
  - PRG: Post/Redirect/Get
- 특수 리다이렉션
  - 결과 대신 캐시를 사용

## 영구 리다이렉션

> 301 308

- 리소스의 URI가 영구적으로 이동
- 원래의 URL을 사용하지 않음, 검색 엔진 등에서 변경을 인지한다.

### 301 Moved Permanently

- **리다이렉트시 요청 메서드가 GET 으로 변하고, 본문이 제거될 수 있다.**

```
POST /books

bookname=oooo&price=10000
```

->

```
301 Moved Permanently
Location: /new-books
```

자동 Redirect ->

```
GET /new-books
```

> 301은 기존 본문도 사라지고 메서드가 GET으로 변하니 바로 등록되는 것이 아닌 바뀐 Html 등을 응답해준다.

->

```
200 OK
```

### 308 Permanent Redirect

- 301과 기능은 같다
- **리다이렉트시 요청 메스드 본문이 유지된다**

```
POST /books

bookname=oooo&price=10000
```

->

```
308 Permanent Redirect
Location: /new-books
```

자동 Redirect ->

```
POST /new-books

bookname=oooo&price=10000
```

->

```
201 Created
```

> 웬만하면 URI가 변경되었다면 요청에 필요한 양식도 바뀌는 경우가 많기 때문에 308은 거의 사용하지 않는다.

## 일시적인 리다이렉션

> 302, 307, 303

- 리소스의 URI가 일시적으로 변경
- 그래서 검색 엔진 등에서 URI를 변경하면 안된다.

### 302 Found

- **리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있다.** == 301??

> GET으로 변경함 애매

### 307 Temporary Redirect

- 302와 기능은 같다
- 리다이렉트시 **요청 메서드와 본문을 유지**한다 (요청 메서드를 변경하면 안됨!!)

> 본문, 메서드 유지

### 303 See Other

- 302와 기능은 값다
- 리다이렉트시 **요청 메서드가 GET으로 변경**한다.

> 무조건 GET으로 변경

## PRG: Post/Redirect/Get

> 일시적인 리다이렉션 - 예시

- POST로 주문후에 웹 브라우저를 새로고침하면??
- 새로고침은 다시 요청
- 중복 주문이 될 수 있다.

```
POST /orders

itemId=book&count1
```

->

주문 데이터 DB 저장

```
200 OK

<html>OK</html>
```

결과 화면에서 새로고침

->

마지막 요청인 POST 요청을 보냄

```
POST /orders

itemId=book&count1
```

->

```
200 OK

<html>OK</html>
```

주문 데이터 DB 저장

**이렇게 중복 주문 문제가 일어난다**

- POST로 주문 후 새로고침으로 인한 중복 주문 방지
  - 물론 서버단에서 막아야함
- **POST로 주문후에 주문결과 화면을 GET 메서드로 리다이렉트 한다 PRG**
- 새로고침해도 결과화면을 GET한다
- 중복 주문 대신 결과화면만 GET한다

```
POST /orders

itemId=book&count1
```

->

주문 데이터 DB 저장

```
302 Found
Location: /order-result/100
```

->

Location 경로로 자동 디라이렉트

결과화면에서 새로고침

```
GET /order-result/100
```

->

```
200 OK

<html>OK</html>
```

- PRG 이후 리다이렉트
  - URL이 이미 POST -> GET으로 리다이렉트 된다
  - 새로고침 해도 GET으로 결과화면만 조회한다.

## 그래서 뭘 써야함??

**302 307 303**

- 302 Found - GET으로 변할 수 있음
- 307 Temporary Redirect - 메서드가 변하면 안됨
- 303 See Other - 메서드가 GET으로 변경됨

역사

- 처음 302 스팩의 의도는 HTTP 메서드를 유지하는 것이다
- 그런데 웹 브라우저 대부분 GET으로 바꾸어버렸다
- 그래서 모호한 302를 대신하기 위해 명확한 307, 303이 등장함 (301 대응으로 308도 등장)

현실

- 307, 303을 권자아하지만 현실적으로 많은 애플리케이션 라이브러리들이 302를 기본값으로 사용한다
- 자동 리다이렉션시에 GET으로 변해도 되면 그냥 302를 사용해도 큰 문제 없다

## 기타 리다이렉션

> 300 304

### 300 Multiple Choices 안쓴다

### 304 Not Modified

- 캐시를 목적으로 사용
- 클라이언트에게 리소스가 수정되지 않았음을 알려준다, 따라서 클라이언트는 로컬 PC에 저장된 캐시를 재사용한다. (캐시로 리다이렉트)
  > 서버야 이거 이미지 캐시 기간 다 된거같은데 새로주셈 -> ㄴㄴ 니 컴퓨터 로컬 캐시 쓰셈 304
- 304 응답은 응답에 메시지 바디를 포함하면 안된다 (로컬 캐시를 사용한다)
- 조건부 GET, HEAD 요청시 사용
