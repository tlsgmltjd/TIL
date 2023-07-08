## axios

-> `JavaScript` 기반의 HTTP 클라이언트 라이브러리로, 웹 애플리케이션과 서버 간의 데이터 통신을 간편하게 처리해준다!

- 일반적으로 자바스크립트에서 API를 연동하기 위해 Fetch API를 사용했다.
- 하지만 여러 특징 때문에 리엑트에서 개발을 할 땐 `axios` 를 사용하는 것을 선호한다.

### 특징

- Promise 기반이다.
  > 비동기적인 요청과 응답 처리를 지원
- HTTP 요청과 응답을 JSON 형태로 자동 변경
- 간결하고 직관적이다

---

```
npm i axios
```

---

### GET

```js
axios.get(url, { config });
```

> ex

```js
axios
  .get("/api/data", {
    headers: {
      "Content-Type": "application/json",
      Authorization: "Bearer TOKEN",
    },
  })
  .then((response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```
