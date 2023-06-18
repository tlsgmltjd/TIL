## useTitle

```jsx
import { useEffect, useState } from "react";

export default function useTitle(initalTitle) {
  // initalTitle를 파라미터로 받아 title state에 초기화
  const [title, setTitle] = useState(initalTitle);

  // hmtl title 테그의 값을 title state 값으로 대입한다.
  const updateTitle = () => {
    const htmlTitle = document.querySelector("title");
    htmlTitle.innerText = title;
  };

  // updateTitle를 컴포넌트가 Mount, title state가 변경될 때마다 실행한다.
  useEffect(updateTitle, [title]);

  // title state의 setter 함수를 리턴한다.
  return [setTitle];
}
```

```jsx
import useTitle from "./Hooks/useTitle";

function App() {
  // title의 초기값은 "Loading..."
  const [titleUpdater] = useTitle("Loading...");

  // 5초 뒤 useTitle 훅의 리턴으로 받아온 title setter 함수로 title을 "home" 으로 변경함
  setTimeout(() => {
    titleUpdater("home");
  }, 5000);

  return <div></div>;
}
```
