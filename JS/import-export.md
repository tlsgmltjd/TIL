## import / export

- import, export로 변수나 함수, 클래스를 `export` 하고 다른 스크립트에서 해당 모듈을 `import` 하여 사용할 수 있게 한다.

* **한 개의 모듈 `export / import` 하기**

```js
export default `내보낼 것`;
```

```js
import `받아올 것` from `'경로'`
```

- **여러개의 모듈 `export / import` 하기**

```js
export {`내보낼 것1`, `내보낼 것2`};
```

```js
import {`받아올 것1`, `받아올 것2`};
```

- 여러개의 파일을 이름 지어 모두 `import` 하기

```js
import { * as `받아올 것 들` }
```

---

```js
// (library.js)

let a = 10;
export default a;
```

```html
// (index.html)

<script type="module">
  import a from "library.js";
  console.log(a);
</script>
```

> JS 파일에선 이렇게 사용할 수 있다.

- export default `내보낼 것`
- import `받아올 것` from `'경로'`
