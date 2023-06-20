## useRef

- `useRef`는 **저장공간** 또는 **DOM요소에 접근**하기 위해 사용되는 `React Hook`이다.

  > Ref는 reference, 즉 참조라는 뜻이다.

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
