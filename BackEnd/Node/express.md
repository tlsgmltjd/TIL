## express

- 서버 프로그래밍을 위한 프레임워크이다.

```
npm i express
```

---

- http를 사용하여 서버를 띄우면 간단한 서버에도 많고 복잡한 코드 작성이 필요한다.
- 미들웨어를 사용하지 않는다.

* Node 백엔드 공부할 땐 좋은 `express 프레임워크` 공부하자

> http로 띄운 서버

```js
const http = require("http");
const app = http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/html; charset=utf-8" });
  if (req.url === "/") {
    res.end("여기는 루트");
  } else if (req.url === "/login") {
    res.end("여기는 로그인");
  }
});

app.listen(3001, () => {
  console.log("http로 가동된 서버입니다.");
});
```

> **express**로 띄운 서버

```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("여기는 루트 입니다.");
});

app.get("/login", (req, res) => {
  res.send("여기는 로그인 입니다.");
});

app.listen(3000, () => {
  console.log("서버 가동");
});
```

---

> ex

```js
const express = require("express"); // express 불러옴
const app = express();
const port = 3000;

app.listen(port, () => {
  console.log("서버 구동");
});

app.get("/", (req, res) => {
  res.send("Hello World!");
});
```
