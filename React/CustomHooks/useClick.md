## useClick

```jsx
import { useEffect, useRef } from "react";

export default function useClick(onClick) {
  const element = useRef();

  useEffect(() => {
    // element에 current 값이 있다면
    if (element.current) {
      // 해당 요소에 click 이벤트를 등록하고 파라미터로 받은 onClick 함수를 실행한다.
      element.current.addEventListener("click", onClick);
    }

    // 해당 컴포넌트가 willUnMount 될 때 해당 요소에 등록 되어있는 이벤트 리스너를 clean-up 한다.
    return () => {
      if (element.current) {
        element.current.removeEventListener("click", onClick);
      }
    };
  }, []);

  return element;
}
```

```jsx
import useClick from "./Hooks/useClick";

function App() {

    // click 했을 때 실행할 함수
  const handleOnClick = () => console.log("Hello!!!");

  const title = useClick(handleOnClick);

  return (
    <div>
      <h1 ref={title}>Hi</h1>
    </div>
  );
```
