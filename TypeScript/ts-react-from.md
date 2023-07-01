```ts
import { useState } from "react";

function App() {
  const [value, setValue] = useState<string>("");

  const onChange = (e: React.FormEvent<HTMLInputElement>) => {
    const {
      currentTarget: { value },
    } = e;
    setValue(value);

    console.log(value);
  };

  // `event`는 `form`에서부터 왔다. -> `FormEvent`
  // 어떤 Element가 이벤트를 발생시키는가? -> `<HTMLFormElement>`
  const onSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    console.log(`Hello ${value}`);
  };

  return (
    <div>
      <form onSubmit={onSubmit}>
        <input
          value={value}
          onChange={onChange}
          type="text"
          placeholder="username"
        />
        <button>Log in</button>
      </form>
    </div>
  );
}

export default App;
```
