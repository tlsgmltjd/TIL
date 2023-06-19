## useFadeIn

```jsx
import { useEffect, useRef } from "react";

export const useFadeIn = (sec = 1, delay = 0) => {
  // element ref 를 리턴해서 요소를 지정
  const element = useRef();

  useEffect(() => {
    // 요소가 지정되었다면
    if (element.current) {
      const { current } = element;
      // trainsition 등록하기
      current.style.transition = `opacity ${sec}s ease-in-out ${delay}s`;
      current.style.opacity = 1;
    }
  }, []);

  // ref 속성과 style 속성을 {} 객체 형태로 리턴함
  return { ref: element, style: { opacity: 0 } };
};
```

```jsx
function App() {
  const fadeInH1 = useFadeIn(2, 2);
  const fadeInP = useFadeIn(4, 3);

  return (
    <div>
      <h1 {...fadeInH1}>Hello</h1>
      <p {...fadeInP}>kjflksdjflksdjfsldkf</p>
    </div>
  );
}
```
