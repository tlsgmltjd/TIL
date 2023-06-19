## fetch

- `fetch` 는 **HTTP 요청 전송 기능을 제공하는 Web API**이다.

```jsx
fetch("https://jsonplaceholder.typicode.com/posts/1").then((response) =>
  console.log(response)
);
```

#### 1. fetch 함수는 `Promise` 객체를 리턴한다.

#### 2. `Promise` 객체의 then 메소드로, '리스폰스가 왔을 때 실행할 콜백'을 등록할 수 있다.

#### 3. 이렇게 등록된 콜백들은 then 메소드로 등록한 순서대로 실행되고, 이때 이전 콜백의 리턴값을 이후 콜백이 넘겨받아서 사용할 수 있다.

> fetch 함수가 반환한 Promise 객체

```
Response {type: 'cors', url: 'https://jsonplaceholder.typicode.com/posts/1', redirected: false, status: 200, ok: true, …}
```

---

### Get 요청

> fetch함수는 디폴트로 GET 방식으로 작동한다.

```js
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

```js
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit↵suscipit recusandae consequuntur …strum rerum est autem sunt rem eveniet architecto"
}
```

- 응답객체는 json() 메서드를 제공하고, 이 메서드를 호출하면 응답객체로부터 JSON 형태의 데이터를 자바스크립트 객체로 변환하여 얻을 수 있다.

> `JSON` -> `Object`

### POST 요청

```js
fetch(`${BASE_URL}api/color-surveys`, {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    mbti: "ENFP",
    colorCode: "#123123",
    password: "0301",
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

- **method 옵션**을 `POST`로 지정해주고, **headers 옵션**으로 `JSON` 포맷 사용한다고 알려줘야 함 `"Content-Type": "application/json",`

* body 옵션에는 요청 보낼 데이터들을 JSON 형식으로 넣어준다.
  > JSON.stringify() 함수 안에 JS Object를 넣어 JSON 형식으로 변환

#### Content-Type 헤더?

- Content-Type 헤더는 현재 리퀘스트 또는 리스폰스의 바디에 들어 있는 데이터가 **어떤 타입인지** 나타낸다.
- **'주 타입(main type)/서브 타입(sub type)'** 형식
  > text/plain, text/javascript, image/png.. 등등

* **JSON 데이터** : `application/json`

### PUT 요청

```js
fetch(URL), {
  method: "PUT",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "Title_1",
    body: "asdslkdfjslkdjfklsdjfkl",
    id: 1,
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

- 데이터를 **수정(덮어쓰기)하기 위해** 사용되며, `method` 옵션만 **PUT으로 설정**한다는 점 빼놓고는 POST 방식과 비슷

### DELETE 요청

```js
fetch("https://jsonplaceholder.typicode.com/posts/1", {
  method: "DELETE",
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```
