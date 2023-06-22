## react - style

### CSS

- 가장 기본이 되는 방법으로 **Component에서 css파일을 import** 하여 사용하는 방법이다.

```jsx
import "styles.css";

const App = () => {
  return <div className="App">...</div>;
};
```

> 가장 간단한 방법이기 때문에 적용하기는 쉽다.

> 하지만 어플리케이션의 **규모가 커질수록** **컴포넌트가 많아지며**, **css 파일을 관리하기도 어려워지고** 여러 컴포넌트에서 사용한 **`Class Name`들의 중복**이 발생할 수 있다.

---

### CSS Module

- React에서 기본으로 제공하는 **CSS module** 이용하는 방법이고,  
  `Class Name` 중복 문제를 해결할 수 있다.

- **css 파일의 확장자를 .module.css로 작성**하여 사용할 수 있다.

```jsx
import styled from "./App.module.css";

const App = () => {
  return (
    <>
      <h1 className={styled.text}>Hello</h1>
    </>
  );
};

export default App;
```

```css
/* App.module.css */

.text {
  text-weight: 700;
}
```

> CSS Module 방식을 이용하고 프로젝트를 실행해보면 `Class Name`이 중복되지 않게,
> **고유한 이름을 지어주어 중복을 막아준다.**

---

### Styled-Components

- Styled-Components는 **React 컴포넌트를 사용하여 스타일을 작성**하는 방식이고 JavaScript 코드 안에 작성된다.

- `Styled-Components`를 사용하면 기존 CSS 를 사용할 때 발생했던 문제점들을 막을 수 있다.

  - CSS 클래스 이름이 겹치는 문제
  - 재사용하는 CSS 코드를 관리하기 어려운 문제
    > 등등..

> [styled-components](<(https://github.com/tlsgmltjd/TIL/blob/main/React/styled-components.md)>)
