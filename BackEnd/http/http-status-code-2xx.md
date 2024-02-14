# 2xx 성공 Successful

> 클라이언트의 요청을 성공적으로 처리

- 200 OK
- 201 Craeted
- 202 Accepted
- 203 No Content

## 200 OK

> 요청 성공

```
GET /books/100 HTTP/1.1
Host: localhost:8080
```

->

```
HTTP/1.1 200 OK
```

## 201 Created

> 요청 성공해서 새로운 리소스가 생성됨

```
POST /books/100 HTTP/1.1
Content-Type: application/json

{
    "bookname" : "오브젝트",
    "price" : 10000
}
```

->

```
HTTP/1.1 201 Created
Location: /books/101
```

## 202 Accepted

> 요청이 접수되었으니 처리가 완료되지 않음

- 배치 처리 같은 곳이 사용
- ex. 요청 후 몇시간 뒤에 배치 프로세스가 요청을 처리할때

## 203 No Content

> 서버가 요청을 성공적으로 수행했지민, 응답 페이로드 본문에 보낼 데이터가 없음

- ex. 웹 문서 편집기에서 save 버튼
- 버튼 클릭 결과로 아무 내용이 없어도 된다
- 저장 버튼을 눌러도 같은 화면이 유지된다
- 결과 내용이 없어도 204 메시지만으로 성공을 인식할 수 있다
