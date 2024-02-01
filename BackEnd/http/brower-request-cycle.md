# 웹 브라우저 요청 흐름

```
https://www.google.com:443/search?q=backend&hl=ko
```

해당 URL을 브라우저에 요청하는 흐름에 대해 설명해보겠다.

---

해당 URL의 도메인명을 DNS 조회를 하여 IP를 알아낸다.

IP와 포트정보를 찾아낸 후 HTTP **요청 메시지**를 생성한다.

```
GET /search?q=backend&hl=ko HTTP/1.1
Host: www.google.com
```

> HTTP 요청 메시지

### HTTP 메시지 전송

1. 웹 브라우저가 HTTP 메시지 전송
2. SOCKET 라이브러리를 통해 전달

- TCP/IP연결
- 데이터 전달

3. TCP/IP 패킷 생성 + HTTP 요청 메시지
4. 인터넷으로 전송됨

수 많은 노드를 거처 구글 서버로 도착한다.

구글 서버에서는 도착한 패킷의 HTTP 메시지를 해석한다.

요청 메시지를 해석한 대로 구글 서버에서 **HTTP 응답 메시지**를 생성한다.

```
HTTP/1.1 200 OK
Content-Typr: text/html;charset=UTF-8
Content-Length: 3000

<html>...
```

> HTTP 응답 메시지

응답 메시지에서 요청과 똑같이 TCP/IP 패킷을 만들어 요청한 웹 브라우저에 응답해준다.

받은 응답 메시지의 html을 화면에 랜더링 해준다.
