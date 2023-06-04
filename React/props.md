## Props

- property(속성)의 복수형

* component의 속성을 의미 → **component에 전달할 정보**를 담고 있는 자바스크립트 객체이다.

- **⭐Read-Only**

```jsx
import React from "react";

function Hello(props) {
  return <div>안녕하세요 {props.name}</div>;
}

function App() {
  return <Hello name="react" />;
}

export default App;
```

- `App 컴포넌트`에서`Hello 컴포넌트`를 사용 할 때 `name` 이라는 값을 전달하는 과정이다.

---

```jsx
import React from "react";

function Hello({ name }) {
  return <div>안녕하세요 {name}</div>;
}

function App() {
  return <Hello name="react" />;
}

export default App;
```

> 이렇게 구조분해할당 문법을 적용할 수 있음
