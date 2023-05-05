## HTTP?

---

### HTTP (HyperText Transfer Protocol)

- HTML 문서와 같은 문서들을 가져올 수 있는 텍스트 기반의 통신 규약이며 인터넷에서 데이터를 주고받을 수 있는 프로토콜(규약)이다.  
  이렇게 규약을 정해두었기 때문에 모든 프로그램이 이 규약에 맞춰 서로 정보를 교환할 수 있게 되었다.

### HTTP 동작

클라이언트가 요청을 하면 서버에서는 해당 요청사항에 맞는 결과를 찾아서 사용자에게 응답하는 형태로 동작한.

`요청 : client -> server`
`응답 : server -> client`

---

### Request (요청)

- 클라이언트가 서버에게 정보를 달라고 하는 것

* 보낼때는 요청에 대한** 정보**를 담아 서버로 보낸다.

### Request Method (요청의 종류)

**GET** : 자료를 요청<br />
**POST** : 자료의 생성을 요청<br />
**PUT** : 자료의 수정을 요청<br />
**DELETE** : 자료의 삭제를 요청<br />

### Request 의 예시

<code>GET URL HTTP/1.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...
Upgrade-Insecure-Requests: 1
</code>
<code>
(본문)
</code>
<br />

- 첫째줄  
  GET : HTTP Method  
  URL : 사이트 주소  
  HTTP/1.1 : HTTP 버전

- 둘째줄~ (헤더)  
  요청에 대한 정보를 담고 있다. User-Agent, Upgrade-Insecure-Requests 등등이 헤더의 종류는 매우 많다.

- 헤더에서 한 줄 띄고 (본문)  
  본문은 **요청을 할 때 함께 보낼 데이터를** 담는 부분이다.

---

### Response (응답)

- 서버가 요청에 대한 답변을 클라이언트에게 보내는 것

### Status Code (상태 코드)

- 1XX 정보응답 : 요청을 받았으며 작업을 계속한다.
- 2XX 성공응답 : 클라이언트가 요청한 동작을 수신하여 이해했고 승낙했으며 성공적으로 처리했음을 가리킨다.
- 3XX 리다이렉션 메세지 : 클라이언트는 요청을 마치기 위해 추가 동작을 취해야 한다.
- 4XX 클라이언트 에러 : 클라이언트에 오류가 있음을 나타낸다.
- 5XX 서버 에러: 서버가 유효한 요청을 명백하게 수행하지 못했음을 나타낸다.

### Resonse 예시

<code>HTTP/1.1 200 OK
Content-Type: text/html;
[HTML]
</code>

- 첫째줄 : 버전 상태코드 상태메시지

- 둘째줄~ : 헤더로 응답에 대한 정보

- 헤더 뒤부터 : 요청한 데이터가 들어있다. (HTML 등)
