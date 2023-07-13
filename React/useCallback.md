## useCallback

- 특정 함수를 계속해서 새로 만들지 않고 재사용하고 싶을 때 사용한다
- 메모제이션된 함수를 반한하는 하는 함수이다!!!

### useMemo 훅과 차이점

- `useMemo` : 특정 결과값을 재사용
- `useCallback` : 특정 함수를 재사용

```js
useCallbak(function, [deps]);
```

---

```js
import { useCallback, useEffect, useState } from "react";

function App() {
  const [number, setNumber] = useState(0);
  const [toggle, setToggle] = useState(true);

  const myFunction = useCallback(() => {
    console.log(number);
  }, [number]);

  useEffect(() => {
    alert("myFunction");
  }, [myFunction]);

  return (
    <div>
      <input
        type="number"
        value={number}
        onChange={(e) => {
          setNumber(e.target.value);
        }}
      />
      <br />
      <button onClick={myFunction}>clcik me</button>
      <br />
      <button onClick={() => setToggle(!toggle)}>{toggle.toString()}</button>
    </div>
  );
}

export default App;
```

```js
const myFunction = () => {
  alert(number);
};
```

> 이렇게 사용했다면 toggle state가 변경 되었을 때도 함수가 초기화 되어 useEffect 훅이 실행되었을 것이다.

> 함수를 useCallbak으로 감싼 후 의존성 배열에 number을 넣으므로써 number가 바뀔 때만 함수가 업데이트 되게 하였다.

---

```js
import { useCallback, useEffect, useState } from "react";

function Box({ createBoxStyle }) {
  const [style, setStyle] = useState({});

  useEffect(() => {
    console.log("useEffect 가 불려용");
    setStyle(createBoxStyle());
  }, [createBoxStyle]);

  return <div style={style}></div>;
}

function App() {
  const [size, setSize] = useState(100);
  const [isDark, setIsDark] = useState(false);

  // isDark state 가 변해도 리랜더링 되어 createBoxStyle가 다시 선언되고
  // useEffect가 불리기 때문에
  // size state 가 불렸을 때만 초기화가 되어야 하므로
  // useCallbak 훅의 의존성 배열에 size를 넣음!
  const createBoxStyle = useCallback(() => {
    return {
      backgroundColor: "pink",
      width: `${size}px`,
      height: `${size}px`,
    };
  }, [size]);

  return (
    <div style={{ background: isDark ? "black" : "white" }}>
      <input
        type="number"
        value={size}
        onChange={(e) => {
          setSize(e.target.value);
        }}
      />
      <button
        onClick={() => {
          setIsDark(!isDark);
        }}
      >
        T
      </button>
      <Box createBoxStyle={createBoxStyle} />
    </div>
  );
}

export default App;
```

```js
const createBoxStyle = () => {
  return {
    backgroundColor: "pink",
    width: `${size}px`,
    height: `${size}px`,
  };
};
```

> 이 함수는 isDark state가 변경 되어도 초기화 되어 useEffect 훅이 실행된다.

> useCallbak으로 감싸고 의존성 배열에 size state를 넣으므로써 size state가 변할 때만 함수가 업데이트 되게 하였다.
