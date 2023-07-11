## useContext

- `Props`만으로 리액트 개발을 하다 보면 여러 곳에 쓰이는 데이터를 내려주고 싶을 때, 컴포넌트의 단계가 많다면 여**러 번 반복해서 Prop을 내려줘야하는 `Props Drilling` 문제가 발생한다.**

- `Context`는 프롭 드릴링을 해결할 수 있으며 **전역상태관리**를 할 수 있다.

> **전역상태관리** : 특정 컴포넌트에서의 state 변화를 전역상태에 저장해두고,필요한 컴포넌트에서 사용 하는 것이다.

---

### Context 만들기

```jsx
import { createContext } from "react";

const ThemeContext = createContext(Null);
```

- `Context`는 `createContext` 라는 함수를 통해 만든다.

  > 기본값을 넣어줄 수도 있다.

### Context 적용하기

- `Context`를 쓸 때는 반드시 값을 **공유할 범위**를 정해야한다.

* 범위는 `Context` 객체에 있는 **`Provider` 라는 컴포넌트로 정해줄 수 있다.**

- **`Provider`의 `value` prop으로 공유할 값을 내려준다.**

```jsx
function App() {
  return (
    <ThemeContext.Provider value="Dark">
      ... Provider 안의 컴포넌트에서는 ThemeContext 사용가능
    </ThemeContext.Provider>
  );
}
```

### Context 값 사용하기

- **`useContext` 라는 Hook을 사용하면 값을 가져와 사용할 수 있다.**

* 이때 아규먼트로는 사용할 Context를 넘겨준다.
  > ThemeContext

```jsx
const Header = () => {
  const data = useContext(ThemeContext);

  return <h1>{data}</h1>;
};
```

---

#### Dark Mode

- **ThemeContext**

```jsx
import { createContext } from "react";

// createContext의 초기값은
// 상위 컴포넌트에 <ThemeContext.Provider> ... 로 감싸주지 않았을 때 받아지는 값이다.
export const ThemeContext = createContext(null);
```

- App

```jsx
import { useState } from "react";
import { Page } from "./components/Page";
import { ThemeContext } from "styled-components";

const App = () => {
  const [isDark, setIsDark] = useState(false);

  return (
    <ThemeContext.Provider value={{ isDark, setIsDark }}>
      <Page />;
    </ThemeContext.Provider>
  );
};

export default App;
```

- Page

```jsx
import { Content } from "./Content";
import { Footer } from "./Footer";
import { Header } from "./Header";

export const Page = () => {
  return (
    <div className="page">
      <Header />
      <Content />
      <Footer />
    </div>
  );
};
```

- Header

```jsx
import { useContext } from "react";
import { ThemeContext } from "styled-components";

export const Header = () => {
  const data = useContext(ThemeContext);

  const { isDark } = data;

  return (
    <header
      className="header"
      style={{
        backgroundColor: isDark ? "#2d333b" : "lightgray",
        color: isDark ? "white" : "black",
      }}
    >
      <h1>HEADER</h1>
    </header>
  );
};
```

- Content

```jsx
import { useContext } from "react";
import { ThemeContext } from "styled-components";

export const Content = () => {
  const data = useContext(ThemeContext);

  const { isDark } = data;

  return (
    <main
      className="content"
      style={{
        backgroundColor: isDark ? "#545d68" : "white",
        color: isDark ? "white" : "black",
      }}
    >
      <p>Content</p>
    </main>
  );
};
```

- Footer

```jsx
import { useContext } from "react";
import { ThemeContext } from "styled-components";

export const Footer = () => {
  const data = useContext(ThemeContext);

  const { isDark, setIsDark } = data;

  const toggleTheme = () => {
    setIsDark(!isDark);
  };

  return (
    <footer
      className="footer"
      style={{
        backgroundColor: isDark ? "#2d333b" : "lightgray",
      }}
    >
      <button className="Button" onClick={toggleTheme}>
        DarkMode
      </button>
    </footer>
  );
};
```
