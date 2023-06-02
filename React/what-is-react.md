## React

- `React`는 `웹 프레임워크`이며 사용자 인터페이스를 구성하기 위한 자바스크립트 라이브러리이다.

### 쓰는 이유?

- html과 css, javascript를 이용해서 웹 페이지를 만들 수 있지만,  
  `가독성과 유지보수성`, 그리고 컴포넌트별로 쪼개 `재사용`이 가능한 점들과  
  `사용자와 상호작용할 수 있는 동적인 UI`를 쉽게 만들 수 있다는 것들 때문에 이용된다.

### React의 특징

### Data Flow

- `react`는 데이터의 흐름이 `한 방향`으로만 흐르는 `단방향 데이터 플로우`이다.

* `단방향 데이터 플로우`의 장점은 데이터의 흐름이 예측 가능하고 추적하기 쉽다는 것이다.

- react는 상위 컴포넌트에서 하위 컴포넌트로 데이터를 전달하고 업데이트하는 방식을 사용한다.  
  **이를 통해 데이터의 흐름을 예측 가능하고 추적하기 쉽게한다.**

### Component 기반 구조

- React는 UI를 여러 컴포넌트로 쪼개서 만든다.

* 한 페이지 내에서도 여러 각 부분을 독립된 컴포넌트로 만들고,  
  이 컴포넌트를 조립해 화면을 구성한다.

- 컴포넌트 단위로 쪼개져 있기 때문에, 전체 **코드를 파악하기가 상대적으로 쉬우며** 이렇게 관리한 컴포넌트를 **재사용, 유지보수하는 것이 쉽다.**

```jsx
const MainPage = () => {
  return (
    <S.MainPage>
      <S.Content>
        <S.Description>React</S.Description>
      </S.Content>
    </S.MainPage>
  );
};
```

### Virtual DOM

> Virtual DOM은 가상의 Document Object Model 이다.

- 이벤트가 발생할 때마다 `Virtual DOM`을 만들고, UI를 다시 그릴 때마다 `실제 DOM`과 비교하고 전후 상태를 비교해, **변경이 필요한 최소한의 변경사항**만 실제 DOM에 반영하여 앱의 효율성을 높히는 방식이다.

### Props and State

**Props**

- 부모 컴포넌트에서 자식 컴포넌트로 전달해 주는 데이터이다.

**State**

- 컴포넌트에서 사용되는 변수 같은 것으로, 값을 변경할 수 있고  
  이를 통해 UI의 상태를 관리하며 업데이트할 수 있다.

### JSX

- Javascript를 확장한 문법이며, JavaScript 코드 안에 HTML과 유사한 문법으로 UI 구조를 작성할 수 있다.

```jsx
const App = () => {
  const name = "John Doe";
  const message = <p>Hello, {name}!</p>;

  return (
    <div>
      <h1>Welcome to My App</h1>
      {message}
    </div>
  );
};
```

`{ }` 중괄호를 사용하여 변수나 표현식을 JSX에 삽입할 수 도 있다.
