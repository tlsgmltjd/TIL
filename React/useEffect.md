## useEffect

컴포넌트가 `Mount`, `Update`, `Unmount` 되었을 때 코드를 실행하고 싶을 때 사용한다.

> 많이 사용하는 사례는  
> **데이터 가져오기**, **상태 업데이트**, **구독 및 정리**에 사용된다.

```jsx
useEffect(() => {});
```

- `useEffect` 훅의 기본 형이다.

---

### useEffect 훅 형태

#### 1

```jsx
useEffect(() => {});
```

> 컴포넌트가 `Mount` 될 때와 `Update` 될 때마다 실행된다.

#### 2

```jsx
useEffect(() => {}, []);
```

> 컴포넌트가 `Mount` 될 때만 실행된다.

#### 3

```jsx
useEffect(() => {}, [dependency]);
```

> 컴포넌트가 `Mount` 될 때와 **디펜던시 리스트**의 값이 변경 될 때 마다 실행된다.

### CleanUp

```jsx
useEffect(() => {
  // 컴포넌트 마운트 시 작업 수행

  return () => {
    // 컴포넌트 언마운트 또는 업데이트 전에 작업 정리
  };
}, []);
```

> `useEffect` 훅 내부에 return 값으로 함수를 넘겨주면  
> 해당 컴포넌트가 `Unmount` 될 때와 `Update 되기 전`에 실행된다.

> 즉, 이 함수는 정리 작업을 담당하게 된다.

---

> Clean-Up 예시

```jsx
import React, { useEffect } from "react";

function MyComponent() {
  useEffect(() => {
    const timer = setInterval(() => {
      console.log("Timer running");
    }, 5000);

    return () => {
      clearInterval(timer);
    };
  }, []);

  return <div>진헌이</div>;
}
```

- 컴포넌트가 `Unmount` 될 때 타이머가 정리된다.

* 이 작업을 통해 컴포넌트가 더 이상 렌더링되지 않을 때 불필요한 타이머 작동을 정리한다!
