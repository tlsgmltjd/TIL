## Router

- 리액트에서 경로에 따라 페이지를 나누도록 해주는 라이브러리이다.

```
$ npm install react-router-dom
```

---

### 라우터 사용하기

- 라우터를 사용하려면 최상위 컴포넌트에 `BrowserRouter` 를 감싸주어 사용한다.

```ts
import { BrowserRouter } from "react-router-dom";

function App() {
  return <BrowserRouter>...</BrowserRouter>;
}
```

### 페이지 나누기

- `Routes` 컴포넌트 안에 `Route` 를 배치하여 각 페이지를 나눈다.
- 위에서부터 차례로 **현재 경로와 `path`**, **`prop`이 일치하는 Route 찾는다.**

```ts
<Routes>
  <Route path="/" element={<HomePage />} />
  <Route path="posts" element={<PostPage />} />
</Routes>
```

#### 하위 페이지 나누기

- `Route` 컴포넌트 안에 `Route` 컴포넌트를 배치하면 된다.
- 이때 **하위 페이지에서 최상위 경로에 해당하는 경로**는 **`index`** 라는 props를 사용한다.

```ts
<Routes>
  <Route path="/">
    <LoginPage />
  </Route>
  <Route path="main">
    <Route index element={<MainPage />} />
    <Route path="/cart" element={<CartPage />} />
  </Route>
</Routes>
```

### 페이지 이동하기

#### 링크

- 리엑트 라우터에선 `<a>` 테그 대신 `Link` 컴포넌트로 페이지를 이동시킨다.

- `to` 라는 `prop`으로 이동할 경로를 지정한다.

```ts
<Link to="/main"> 메인화면으로 이동 </Link>
```

### Navigate 컴포넌트

- 리턴값으로 Navigate 컴포넌트를 리턴하면 to prop으로 지정한 경로로 이동한다.

```ts
import { Navigate } from "react-router-dom";

function App() {
  const onClick = () => {
    return <Navigate to="/main" />;
  };

  return (
    <div>
      <button onClick={onClick}>GO</button>
    </div>
  );
}
```

### useNavigate Hook

- useNavigate 라는 hook으로 navigate 함수를 가져오면 이 함수를 통해 페이지 이동이 가능하다.

```ts
const navigate = useNavigate();

...

navigate(/main);
```

### 동적인 경로 다루기

- `콜론 (:)` 으로 시작하는 문자열을 사용하면 경로에 파라미터를 지정할 수 있다.

- 예를 들어 아래처럼 `/:coinId` 라는 경로는 `/123` 이라던지 `/abc` 라는 주소로 접속하면,  
  `123` 이나 `abc` 같은 값을 `coinId` 라는 파라미터로 받는다.

```tsx
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Coins />} />
    <Route path="/:coinId" element={<Coin />} />
  </Routes>
</BrowserRouter>
```

- 경로 파라미터를 사용하려면 `useParams` 라는 훅을 사용하면 된다.

```tsx
function Coin() {
  const { coinId } = useParams<Params>();

  ...
}
```

### 중첩 라우팅

- 서브 페이지처럼 Route 안에 Rouute를 작성할 수 있다.

```js
<Route path="/about" element={<About />}>
  <Route path="shool" element={<Shool />} />
  <Route path="club" element={<Club />} />
</Route>
```

### Outlet
