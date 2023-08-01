## useFullscreen

```tsx
const useFullscreen = (callback: (isFull: boolean) => void) => {
  const element = useRef<HTMLImageElement>();
  const triggerFull = () => {
    if (element.current) {
      element.current.requestFullscreen();
      if (callback && typeof callback === "function") {
        callback(true);
      }
    }
  };
  const exitFull = () => {
    document.exitFullscreen();
    if (callback && typeof callback === "function") {
      callback(false);
    }
  };

  return [element, triggerFull, exitFull];
};
```

> useFullscreen() 훅

- [element, triggerFull, exitFull] 반환
- (callback) 함수를 아규먼트로 받음
  > callback(isFull: boolean)

* `element` 를 FullScreen 시키고 싶은 `element`의 `ref` 속성에 지정
* `triggerFull` `exitFull` 함수 사용
* 전달한 콜백 함수의 파라미터의 값으로 Fullscreen인지 아닌지 확인 가능

```tsx
import { useRef } from "react";
import "./App.css";

function App() {
  const onFullScr = (isFull: boolean) => {
    console.log(isFull ? "FULL" : "NO FULL");
  };

  const [element, triggerFull, exitFull] = useFullscreen(onFullScr);
  return (
    <div>
      <div ref={element}>
        <img src="https://firebasestorage.googleapis.com/v0/b/gwitter-38f80.appspot.com/o/tIhbTYnXFmMbwygcmb7Ss611ltp1%2F7a9fd339-3b8c-41ea-963a-8b928ae40651?alt=media&token=a8edc1dd-2792-42a3-9a7e-6e82b67ed03f" />
        <button onClick={exitFull}>Exit Fullscreen</button>
      </div>
      <button onClick={triggerFull}>Make Fullscreen</button>
    </div>
  );
}

export default App;
```
