## useInput()

```jsx
import { useState } from "react";

export const useInput = (initialValue, validator) => {
  const [value, setValue] = useState(initialValue);

  const onChange = (event) => {
    const currentValue = event.target.value;

    let willUpdate = true;

    if (typeof validator === "function") {
      willUpdate = validator(value);
    }
    if (willUpdate) {
      setValue(currentValue);
    }
  };

  return { value, onChange };
};
```

> `useInput("초기 값", 유효성 검사 함수)`

> 유효성 검사 함수는 input value를 받는 파라미터가 있어야 함  
> 함수가 true 를 반환시에만 입력이 가능하다.

```jsx
function App() {
  const maxLen = (value) => {
    return value.length < 10;
  };

  const inputValue = useInput("Mr.", maxLen);

  return (
    <div>
      <input value={inputValue.value} onChange={inputValue.onChange}></input>
    </div>
  );
}
```

> `<input {...inputValue}></input>` 이렇게 간단히 표현도 가능하다.
> `
