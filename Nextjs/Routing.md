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
