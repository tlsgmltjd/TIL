## usePreventLeave

```jsx
export const usePreventLeave = () => {
  // 경고 창을 띄운다.
  const listener = (event) => {
    event.preventDefault();
    event.returnValue = "";
  };

  // window.addEventListener("beforeunload", listener);
  // window에 "beforeunload" 이벤트를 등록한다.
  // "beforeunload" 이벤트는 사용자가 페이지를 떠나기 전에 발생한다. listener 콜백함수 실행

  const enablePrevent = () => window.addEventListener("beforeunload", listener);
  const disablePrevent = () =>
    window.removeEventListener("beforeunload", listener);

  return [enablePrevent, disablePrevent];
};
```

```jsx
import { usePreventLeave } from "./Hooks/usePreventLeave";

function App() {
  const [protect, unprotect] = usePreventLeave();

  return (
    <div>
      <button onClick={protect}>protect</button>
      <button onClick={unprotect}>unprotect</button>
    </div>
  );
}

export default App;
```
