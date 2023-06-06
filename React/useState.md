## useState

- React에서 사용자의 반응에 따라, 화면을 렌더링 해주기 위해 사용되는 트리거 역할을 하는 변수이다.

* 함수형 컴포넌트에선 `useState` 훅을 사용하여 state를 관리한다.

```jsx
import { useState } from "react";

// const [state, setterFunction] = useState(기본 state값);
const [number, setNumber] = useState(0);

console.log(number);
// 0
```

> state 선언

```jsx
setNumber(10);
```

> state 변경

---

**React에선 대부분 변하는 `state`를 `const`로 선언한다.**

```jsx
const [number, setNumber] = useState(0);
```

여기서 const에는 **주소 값**이 담겨있다.  
그래서 이 주소값 자체를 변경하는 작업은 불가능하지만,  
변경시키지 않는 다른 작업은 가능하기 때문에 const로 선언이 가능하다.

#### 걍 let으로 선언하면 안됨?

- 말 안듣고 state를 setter함수로 변경 안하고 직접 변경할까봐 그렇다.
