### Styled-Components

- **Styled-Components 라이브러리를 이용**하는 방법이다.

* Styled-Components는 **React 컴포넌트를 사용하여 스타일을 작성**하는 방식이고 JavaScript 코드 안에 작성된다.

* **Styled-Components를 다른 컴포넌트에서 재사용**할 수 있으며, **스타일의 속성을 동적으로 변경**할 수 있다.

* 템플릿 리터럴 문법으로 CSS 코드를 작성하여 사용한다.

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

// 이렇게 구조분해할당 문법을 사용하여 표현도 가능하다.
// color: ${({color}) => color};
```

```jsx
...

const App = () => {
  return (
    <Button color="red" >Hello</Button>
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

### Nesting

### 1. 가상 선택자

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

### 2. 컴포넌트 선택자

```jsx
import styled from "styled-components";
import nailImg from "./nail.png";

const Icon = styled.img`
  width: 16px;
  height: 16px;
`;

const StyledButton = styled.button`
  background-color: #6750a4;
  border: none;
  color: #ffffff;
  padding: 16px;

  & ${Icon} {
    margin-right: 4px;
  }

  &:hover,
  &:active {
    background-color: #463770;
  }
`;
```

- `StyeldButton` 안에 `Icon` 이 배치되어있다.

* **`StyledButton` 컴포넌트 안에서 `Icon` 컴포넌트를 선택해** 별도로 `margin-right: 4px`라는 속성을 지정하는 코드이다.

- 이렇게 **컴포넌트를 선택자로 쓰고 싶을 때**는 `${Icon}`같이 **컴포넌트 자체를 템플릿 리터럴 안에 넣어주면** 된다.

```css
.StyledButton .Icon {
  margin-right: 4px;
}
```

> 기존 CSS로 쓰면 이런 느낌

> **`&`와 자손 결합자를 사용하는 경우**에는 `&`를 생략도 가능하다.

<br />

- `Nesting`은 여러 겹으로 할 수도 있다.

```jsx
const StyledButton = styled.button`
  ... &:hover,
  &:active {
    background-color: #7760b4;

    ${Icon} {
      opacity: 0.2;
    }
  }
`;
```

---

### 상속

### styled() 함수

- **`Styled Components`로 만들어진 컴포넌트를 상속하려면** **`styled()` 함수**를 이용한다.

```jsx
const Button = styled.button`
    ...
`;

const SubmitButton = styled(Button)`
    ...
`;

function App() {
  return (
    <div>
      <SubmitButton>계속하기</SubmitButton>
    </div>
  );
}
```

- **`styled(Button)`** : 이렇게 하면 `SubmitButton`이 `Button`의 스타일을 상속받게된다.

```jsx
const Father = styled.div`
  display: flex;
`;

const Box = styled.div`
  background-color: ${(props) => props.bgColor};
  width: 100px;
  height: 100px;
`;

// 다른 컴포넌트의 스타일을 상속하는 새 컴포넌트를 만들려면
// styled() 생성자에 구성한다.
// Box의 style을 모두 가짐(상속 받음)
const Circle = styled(Box)`
  border-radius: 50px;
`;

function App() {
  return (
    <Father>
      <Box bgColor="teal" />
      <Circle bgColor="tomato" />
    </Father>
  );
}
```

---

### as

- `as` 를 사용하여 다른 엘리먼트로 변경이 가능하다.

```jsx
const Father = styled.div`
  display: flex;
`;

function App() {
  return <Father as="header"></Father>;
}
```

---

### 속성추가

- Styled Components에서는 html 태그의 속성도 지정할 수가 있다.

* `.attrs()`

```jsx
const Father = styled.div`
  display: flex;
`;

const Input = styled.input.attrs({ minLength: 10 })`
  background-color: tomato;
`;

function App() {
  return (
    <Father as="main">
      <Input />
    </Father>
  );
}
```

---

### 에니메이션

- css 코드로 키프레임을 구현할 수 있다.

```html
<div class="ball"></div>
```

```css
@keyframes bounce {
  0% {
    transform: translateY(0%);
  }

  50% {
    transform: translateY(100%);
  }

  100% {
    transform: translateY(0%);
  }
}

.ball {
  animation: bounce 1s infinite;
  ...;
}
```

> `@keyframes`로 키프레임 애니메이션을 선언 `->` `animation` 속성에서 사용

#### styled-components 로 구현

```jsx
import styled, { keyframes } from "styled-components";

// keyframes 함수를 사용
const placeholderGlow = keyframes` 50% { opacity: 0.2; }`;

const Placeholder = styled.div`
  animation: ${placeholderGlow} 2s ease-in-out infinite;
`;
```

- `keyframes` 함수를 이용한다. 이 함수도 마찬가지로 템플릿 리터럴로 사용하는 태그 함수이다.

---
