## Routing

- NextJS에서는 react-route-dom을 사용하지 않고 파일 시스템 기반의 라우팅을 사용한다.

```
pages
    -index.js
    -search.js
    -setting.js
    -404.js

    products
        -index.js
        -[id].js
```

- 파일이름이 곧 경로의 이름이다!

> 파일안에 컴포넌트를 만들고 export default 하면 페이지가 생긴다!

```js
// pages/MainPage

exprot default MainPage() {
    return <>MainPage</>
}
```

### 첫번째 페이지

- `index.js` : 첫번째 페이지 `/`

### 중첩경로

- `products` 폴더 안의 `index.js` : `/products/`

### 다이나믹 라우팅

`[id].js` 이렇게 파일 이름을 `[]` 중괄호로 감싸면 파라미터로 사용할 수 있다.

## `<Link>` 컴포넌트

- Next.js에서는 링크를 연결하는데 `<Link>` 컴포넌트를 사용한다.
- `<a>` _(전체를 다시 로딩 -> 속도 느림 + 깜박)_ 를 사용하는 것 보다 Next.js에서 내부적으로 여러가지 최적화를 해주기 때문에 빠르고 부드러운 페이지 전환이 가능하다.

```ts
<Link href="url"></Link>
```

```ts
import Link from 'next/link';

export default Page() {
  return <Link href="/">go to index</Link>;
}
```

## useRouter() Hook

### 쿼리 사용하기

#### Params

- **`router.query`** 값을 사용하면 페이지 주소에서 **Params 값**이나 **쿼리스트링 값**을 참조할 수 있다.

> `pages/products/[id].js` 페이지에서 `router.query['id']` 값으로 Params `id` 의 값을 가져올 수 있다.

```jsx
import { useRouter } from "next/router";

function Products() {
  const router = useRouter();
  const id = router.query["id"];

  return <>Product #{id} 페이지</>;
}
```

> `/products/123` 에 접속했다면  
> `Products #123 페이지` 출력

---

#### Query String

> `/search?q=후디` url에 접속했을 때,  
> `router.query['q']` 값으로 쿼리스트링 `q`의 값을 가져올 수 있다.

```js
import { useRouter } from "next/router";

export default function Search() {
  const router = useRouter();
  const q = router.query["q"];

  return <>{q} 검색 결과</>;
}
```

> `/search/후디 에 접속했다면`  
> `후디 검색 결과`

---

### 페이지 이동하기

- `router.push()` 메서드를 사용하여 페이지를 이동한다.

```js
import { useRouter } from "next/router";

function Products() {
  const router = useRouter();

  const onClickBtn = () => {
    router.push("/");
  };

  return (
    <div>
      <button onClick={onClickBtn}>메인 페이지로 이동</button>
    </div>
  );
}
```

## 리다이렉트

- `next.config.js` 을 수정해서 특정 주소에 대해서 리다이렉트할 주소를 지정할 수 있다.

> ex) `/item/:id` 라는 주소였지만 /`products/:id` 라는 주소로 바뀌었을 때 유저들이 잘못된 주소로 접속할 가능성이 있음

> `/item/:id` 접속시 -> `products/:id` 이 주소로 리다이렉션 시켜준다.

```js
/** @type {import('next').NextConfig} */
const nextConfig = {
  async redirects() {
    return [
      {
        source: "/items/:id",
        destination: "/products/:id",
        permanent: true,
      },
    ];
  },
};
```

> `permanent` 속성  
> `false` -> 307 Temporary Redirect
> `true` -> 308 리다이렉션 정보 저장 Permanent Redirect

## 404 페이지

- 존재하지 않는 주소로 들어올 경우 404 페이지를 보여준다.
- `pages/404.js` 파일을 만들어 구현할 수 있다.

## 커스텀 App

`pages/_app.js`

- 모든 페이지에 공통적으로 코드를 적용하고 싶다면 커스텀 `App` 컴포넌트를 수정하면 된다.

- `Component`와 `pageProps`가 있다.
- `우리가 만든 페이지`들이 `Component Prop`으로 전달되고 여기에 `내부적으로 필요한 Props`는 `pageProps`라는 값으로 전달된다.

```js
import { GlobalStyle } from "@/style/GlobalStyle";
import "@/styles/globals.css";

export default function App({ Component, pageProps }) {
  return (
    <>
      <GlobalStyle />
      <Component {...pageProps} />
    </>
  );
}
```

## 커스텀 Document

`pages/_document.js`

- `Document` 컴포넌트는 HTML 코드의 뼈대를 수정하는 용도로 사용한다.

- 코드는 React 컴포넌트이지만 일반적인 컴포넌트처럼 동작하진 않는다!
  > useState, useEffect ❌

```js
import { Html, Head, Main, NextScript } from "next/document";

export default function Document() {
  return (
    <Html lang="ko">
      <Head />
      <body>
        <Main />
        <NextScript />
      </body>
    </Html>
  );
}
```
