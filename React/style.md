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

- **Styled-Components 라이브러리를 이용**하는 방법이다.

* Styled-Components는 **React 컴포넌트를 사용하여 스타일을 작성**하는 방식이고 JavaScript 코드 안에 작성된다.

* **Styled-Components를 다른 컴포넌트에서 재사용**할 수 있으며, **스타일의 속성을 동적으로 변경**할 수 있다.

```
$ npm i styled-components
```

```jsx
import styled from "styled-components";

const Container = styled.div`
  width: 300px;
  height: 300px;
  background: orange;
`;

const App = () => {
  return (
    <Container>
      <h1>Hello!</h1>
    </Container>
  );
};

export default App;
```

- `styled.TagName` (ex. styled.div``)의 형태로 새로운 객체를 만들고, 내부에 원하는 스타일을 작성하면 된다.

* 이 방법을 사용하면 컴포넌트와 Style을 한 파일 내에서 관리할 수 있고, `Class Name`의 중복도 발생하지 않는다.

---

### 스타일에 props 적용하기

- `styled-component`를 사용하는 장점 중 하나가 **변수에 의해 스타일을 바꿀 수 있다는 점**이다.

```jsx
const Button = styled.button`
  color: ${(props) => props.color};
`;
```

```jsx
...

const App = () => {
  return (
    <Button color={"red"} >Hello</Button>
  );

...
```

---

### 반응형디자인

- `media-query` 이용하여 반응형 디자인을 할 수 있다.

```jsx
const Container = styled.div`
  width: 200px;

  @media screen and (max-width: 944px) {
    width: 100%;
  }
`;
```

---

## 가상 선택자

```jsx
const Box = styled.div`
  background-color: ${(props) => props.bgColor};

  &:hover {
    background-color: #000000;
  }
`;
```

```jsx
const App = () => {
  return (
    <>
      <Box bgColor={"white"}>Hello</Box>
    </>
  );
};
```

- `&`는 **상위 요소에 스타일을 적용**하는 선택자이다.

- `Styled Components`에서 `&`를 사용하면 **현재 컴포넌트** 자체를 선택할 수 있다.

  > `Box` 컴포넌트에 `:hover` 선택자 등록
