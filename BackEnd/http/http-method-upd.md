# HTTP 메서드 PUT, PATCH, DELETE

## PUT

리소스를 대체

- 리소스가 있으면 대체
- 리소스가 없으면 생성
- 덮어버린다

**클라이언트가 리소스를 식별한다**

- 클라이언트가 리소스의 위치를 알고 URL를 지정한다.

### flow

```
PUT /book/2 HTTP/1.1
Content-Type: application/json

{
    name: "좋은코드 나쁜코드",
    price: 40000
}
```

->

리소스가 있다면 서버의 `/book/2` 의 리소스가 대체된다.

```
{
    name: "좋은코드 나쁜코드",
    price: 40000
}
```

리소스가 없다면 서버에 신규 리소스가 생성된다.

```
{
    name: "좋은코드 나쁜코드",
    price: 40000
}
```

### 리소스를 완전히 대체한다.

```
PUT /book/2 HTTP/1.1
Content-Type: application/json

{
    price: 40000
}
```

->

기존 리소스를 완전히 삭제하고 덮어버리기 때문에 메시지에 보내지 않은 필드는 삭제되어버린다.

PUT은 리소스의 수정보다 기존 리소스를 갈아치우기 위해 사용한다.

```
{
    price: 40000
}
```

## PATCH

- 리소스 부분 변경

```
PATCH /book/2 HTTP/1.1
Content-Type: application/json

{
    price: 40000
}
```

->

이렇게 리소스의 데이터를 부분적으로 변경하려면 PATCH를 사용하면 된다.

> age의 값만 보내도 해당 리소스의 age 필드의 값만 수정됨

```
{
    name: "좋은코드 나쁜코드",
    price: 40000
}
```

## DELETE

- 리소스 제거

```
DELETE /book/2 HTTP/1.1
Host: localhost:8080
```

->

서버에 있는 `/book/2` 위치의 리소스가 제거된다.
