## useBeforeLeave

```jsx
import { useEffect } from "react";

export const useBeforeLeave = (onBefore) => {
  const handle = (event) => {
    // event에서 clientY 속성을 구조분해할당 문법으로 가져와 마우스 Y좌표를 확인한다.
    const { clientY } = event;

    // 마우스 Y좌표가 0이하이면 즉, 마우스가 창 위로 벗어났다면,
    // onBefore 콜백함수를 실행한다.
    if (clientY <= 0) onBefore();
  };

  useEffect(() => {
    // 마우스 커서가 브라우저 창을 벗어날 때 handle 함수가 실행된다.
    document.addEventListener("mouseleave", handle);

    // clean-up
    return () => document.removeEventListener("mouseleave", handle);
  }, []);
};
```

```jsx
function App() {
  const begForLife = () => alert("Plz dont leave");

  useBeforeLeave(begForLife);

  return <div></div>;
}
```
