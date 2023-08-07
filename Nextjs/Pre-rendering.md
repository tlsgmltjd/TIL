## Pre-rendering

웹 브라우저가 페이지를 로딩하기 이전에 렌더링하는 것이다.

> **정적 생성(Static Generation)** 과 **서버 사이드 렌더링(Server-side Rendering)** 으로 나뉜다.

### 정적 생성(Static Generation)

> 프로젝트를 빌드하는 시점에 미리 HTML을 렌더링하는 걸 말한다. 기본적으로 Next.js에서는 모든 페이지를 정적 생성한다.

### `getStaticProps()`

- 객체의 props 프로퍼티로 넘겨줄 Props 객체를 지정하고, 이것을 페이지 컴포넌트에서 사용하면 된다.

```js
export async function getStaticProps() {
  const res = await axios("/products/");
  const products = res.data;

  return {
    props: {
      products,
    },
  };
}

export default function Home({ products }) {
  return <ProductList products={products} />;
}
```

### `getStaticPaths()`

- 다이나믹 라우팅을 하는 페이지를 정적 생성을 할 때에는 어떤 페이지를 정적 생성할지 지정해줘야 한다.
- `paths` 라는 배열에서 각 페이지에 해당하는 정보를 넘겨줄 수 있다.

> ex) id 값이 '1'인 페이지를 정적 생성하려면  
>  `{ params: { id: '1' } }`

- `fallback` 이라는 속성을 사용해서 정적 생성되지 않은 페이지를 처리해 줄 것인지 지정할 수 있다.
  > paths 이외의 경로들에 대해 추후 요청이 들어오면 만들어 줄지 말지. 만다면 404를 리턴

```js
export async function getStaticPaths() {
  return {
    paths: [{ params: { id: "1" } }, { params: { id: "2" } }],
    fallback: true,
  };
}
```

- context 파라미터를 사용해서 필요한 Params(context.params) 값이나 쿼리스트링(context.query) 값을 참조할 수 있다.

> `fallback: true`라고 지정했다면, 필요한 데이터가 존재하지 않을 수 있기 때문에 적절한 예외처리를 해야 한다. `{ notFound: true }` 를 리턴하면 데이터를 찾을 수 없을 때 404 페이지로 이동시킬 수 있다.

```js
export async function getStaticProps(context) {
  const productId = context.params["id"];

  let product;

  try {
    const res = await axios(`/products/${productId}`);
    product = res.data;
  } catch {
    return {
      notFound: true,
    };
  }

  return {
    props: {
      product,
    },
  };
}
```

- `fallback: true` 시에 `getStaticProps()` 를 실행하는 동안 보여줄 로딩 페이지를 이렇게 구현할 수 있다.

```js
export default function Product({ product }) {
  if (!product) {
    return <>로딩 중 ...</>;
  }
  return <>상품 이름: {product.name}</>;
}
```
