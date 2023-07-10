## Helmet

- `react-helmet` 라이브러리를 사용하여 페이지별 SEO 메타태그를 적용할 수 있다.

```
npm i react-helmet
```

```js
import { Helmet } from "react-helmet";
```

> `Helmet` 컴포넌트를 import 해서 사용하면 된다.

```js
function myApp() {
  return (
    <div>
      <Helmet>
        <title>myApp</title>
        <meta name="description" content="페이지 설명" />
      </Helmet>

      <div>
        <h1>myApp</h1>
        <p>Description</p>
        ...
      </div>
    </div>
  );
}
```

- 이렇게 `Helmet` 컴포넌트 내부에서 head 요소를 조작할 수 있다!
