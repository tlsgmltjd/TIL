## useConfirm

```jsx
export default function useConfirm(message = "", callback, rejection) {
  // 유효성 검사
  if (callback && typeof callback !== "function") {
    return;
  }
  if (rejection && typeof rejection !== "function") {
    return;
  }

  const confirmAction = () => {
    // prompt 메세지로 yes를 입력한다면 파라미터로 받아온 callback 함수를 실행시킨다.
    if (prompt(message) == "yes") {
      callback();
    } else {
      // 일치하지 않는다면 파라미터로 받아온 rejection 함수를 실행시킨다.
      rejection();
    }
  };

  // confirmAction 함수를 return 한다.
  return confirmAction;
}
```

```jsx
import useConfirm from "./Hooks/useConfirm";

function App() {
  // useConfirm에 callback function으로 전달할 함수
  const deleteWorld = () => console.log("Deleting the World...");
  // useConfirm에 rejection function으로 전달할 함수
  const abort = () => console.log("Aborted");

  // useConfirm 훅에서 return 받은 confirmAction 함수를 실행시키면 message -> `callback function` or `rejection function` 이 실행된다.
  const confirmDelete = useConfirm(
    "Are you sure? typing 'yes'",
    deleteWorld,
    abort
  );

  return (
    <div>
      <button onClick={confirmDelete}>Delete the World</button>
    </div>
  );
}

export default App;
```
