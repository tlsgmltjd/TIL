## useRef

- `useRef`는 **저장공간** 또는 **DOM요소에 접근**하기 위해 사용되는 `React Hook`이다.

  > Ref는 reference, 즉 참조라는 뜻이다.

```jsx
import { useRef } from "react";

// ...

// useRef 함수로 Ref 객체를 만든다.
const ref = useRef();

// ref Prop에다가 앞에서 만든 Ref 객체를 내려준다.
<div ref={ref}> ... </div>;
```

- `Ref` 객체의 `current` 라는 프로퍼티를 사용하면 DOM 노드를 참조할 수 있다.

## 1. 변수 관리

```jsx
function App() {
  const [count, setCount] = useState(0);
  const countRef = useRef(0);
  let countVar = 0;

  function rendering() {
    setCount(count + 1);
  }

  function increaseRef() {
    countRef.current = countRef.current + 1;
    console.log("countRef : ", countRef.current);
  }

  function increaseVar() {
    countVar = countVar + 1;
    console.log("countVar : ", varCount);
  }

  return (
    <div>
      <div>refCount : {countRef.current}</div>
      <div>varCount : {countVar} </div>
      <br />
      <button onClick={rendering}>렌더!</button>
      <button onClick={increaseRef}>ref 올려</button>
      <button onClick={increaseVar}>var 올려</button>
    </div>
  );
}
```

- useRef를 사용해 값을 저장한 `countRef`

* 변수를 통해 값을 저장한 `countVar`

  가 있다.

`ref 올려` 버튼을 누르면 `countRef` 값이 1 오른다.  
`var 올려` 버튼을 누르면 `countVar` 값이 1 오른다.  
`렌더!` 버튼을 누르면 `count` 값이 1 오르며 화면이 새로 렌더링 된다.

하지만 `ref 올려`와 `var 올려` 버튼을 눌러도 화면엔 표시되지 않는다.

왜냐하면 `useRef`로 관리하는 값은 **값이 변해도 화면이 렌더링되지 않는다.**

> 일반 변수도 마찬가지이다.

하지만, `렌더!` 버튼을 눌러 `state`를 변경하여 화면을 새로 렌더링 하면

**`countRef`** 의 `current` 속성은 변경되어 나타나지만  
**`countVar`의 값은 변하지 않는다.**

렌더링을 한다는 것은 현재 컴포넌트 즉, 함수가 다시 호출되는 것이다.

그러므로 `countVar` 변수는 다시 0으로 초기화 되기 때문에 변경사항이 출력되지 않을 것이다.

하지만 `countRef` 값 즉 useRef 훅으로 생성된 **ref는 컴포넌트의 전 생애주기를 통해 유지**되기 때문에 컴포넌트가 아무리 렌더링이 되도 값이 저장된다.

---

## 2. DOM 노드 참조

```jsx
const App = () => {
  const inputRef = useRef();

  useEffect(() => {
    inputRef.current.focus();
  }, []);

  const handleLoginClick = () => {
    alert("환영합니다! " + inputRef.current.value);
  };

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="username" />
      <button onClick={handleLoginClick}>로그인</button>
    </div>
  );
};
```

> 컴포넌트가 `Mount` 되었을 때 인풋 요소가 `focus` 된다.
