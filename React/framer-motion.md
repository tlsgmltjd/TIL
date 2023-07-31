## framer-motion

- 직관적인 코드로 에니메이션을 쉽게 제작해주는 라이브러리 🦋

```
npm i framer-motion
```

---

### motion

- `Framer-Motion`은 `motion`이라는 컴포넌트를 제공한다.

- `motion` 컴포넌트에 props 를 통해서 애니메이션을 구현할 수 있다.

```js
import { styled } from "styled-components";
import { motion } from "framer-motion";

const Box = styled(motion.div)`
  width: 200px;
  height: 200px;
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 2px 3px rgba(0, 0, 0, 0.1), 0 10px 20px rgba(0, 0, 0, 0.1);
`;

export default function App() {
  return (
    <div>
      <Box
        transition={{ type: "spring", delay: 0.5, damping: 20 }}
        initial={{ scale: 0 }}
        animate={{ scale: 1, rotateZ: 360 }}
      />
    </div>
  );
}
```

### Variants

- `variants` 을 이용하여 애니메이션을 미리 저장하여 사용할 수 있다.

```js
const myVars = {
  start: { scale: 0 },
  end: { scale: 1, rotateZ: 360, transition: { type: "spring", delay: 0.5 } },
};

export default function App() {
  return (
    <>
      <GlobalStyle />
      <Wrapper>
        <Box variants={myVars} initial="start" animate="end" />
      </Wrapper>
    </>
  );
}
```
