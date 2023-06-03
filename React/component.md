## 컴포넌트(Component)

- UI를 재사용 가능한 개별적인 여러 조각으로 나눈 것이다.

### 함수형 컴포넌트

```jsx
function App() {
  retrun(
    <>
      <div></div>
    </>
  );
}
```

- 자바스크립트 함수를 선언하듯이 `function` 으로 컴포넌트를 정의하고, `return` 문에 JSX 코드를 반환한다.

* 함수형 컴포넌트를 사용하면,  
  Hook의 `useState`를 사용해 state 를 관리할 수 있고,  
   `useEffect` 를 사용해 LifeCycle 을 관리할 수 있다.

- 그리고 클래스형 컴포넌트보다 **직관적**이며, 클래스형 컴포넌트에 비해 함수형 컴포넌트가 **비교적 메모리 자원을 적게 사용**한다.

> 이거 쓰셈

### 클래스형 컴포넌트

```jsx
import React, { Component } from "react";

class App extends Component {
  render() {
    return (
      <>
        <div></div>
      </>
    );
  }
}
```

- 클래스 컴포넌트는 **class 키워드**가 필수로 들어가며  
  **Component로 상속**을 받아야하고 **render 메서드**가 반드시 있어야한다.

---

### 컴포넌트 구성 요소

**property(props)**

- 부모 컴포넌트에서 자식 컴포넌트에 전달되는 데이터이다.
  > 프로퍼티값은 자식 컴포넌트에서 수정불가

**state**

- 컴포넌트의 상태를 저장하고 수정 가능한 데이터이다.

**context**

- 부모 컴포넌트에서 생성하여 모든 자식 컴포넌트에게 전달하는 데이터이다.
- Context를 사용하면 중간 컴포넌트를 거치지 않고도 컴포넌트 트리 전체에서 데이터를 공유할 수 있다.
