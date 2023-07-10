## `<Image/>` 컴포넌트

- Next.js에서는 이미지를 사용할 때 Next.js 서버를 한 번 거쳐서 이미지 최적화를 한 다음 사용할 수 있게 `<Image />` 컴포넌트를 지원한다.

- 이때 반드시 `width`와 `height` 값을 지정하거나 또는 `fill`이라는 Prop을 지정해주어야한다.

```js
import Image from "next/image";

export default function Page() {
  return (
    <>
      <div
        style={{
          position: "relative",
          width: "100%",
          height: "300px",
        }}
      >
        <Image
          src="/images/product.jpeg"
          fill
          alt="상품 이미지"
          style={{
            objectFit: "cover",
          }}
        />
      </div>
    </>
  );
}
```

- `fill` 을 사용했을 땐 부모 요소에서 `position: relative`와 같이 포지셔닝 해야한다.
  > fill을 사용할 경우 absolute 포지션으로 배치되기 때문

---

## `<Head />` 컴포넌트

- `<Head />` 태그를 사용하여 html `head` 요소를 조작할 수 있다.

```js
import Head from "next/head";

export default function myApp() {
  return (
    <>
      <Head>
        <title>myApp!</title>
        <link rel="icon" href="/favicon.ico" />
      </Head>
      ...
    </>
  );
}
```
