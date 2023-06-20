## Contorlled / Uncontrolled Component

- **제어 / 비제어 컴포넌트**

React에서는 `입력폼`을 다루는 2가지 방법이 있는데,  
바로 **제어 컴포넌트**와 **비제어 컴포넌트**이다.

### 제어 컴포넌트

- 인풋 태그의 `value` 속성을 지정하고 사용하는 컴포넌트이다
- 리액트에서 인풋의 값을 제어하는 경우로 **리액트에서 지정한 값**과 실제 **인풋 value** 의 값이 항상 같다.

* 이렇게 하면 인풋에 쓰는 값을 여러 군데서 쉽게 바꿀 수 있다는 장점이 있어서 리액트에서 권장하는 방법이다

```jsx
function TripSearchForm() {
  const [values, setValues] = useState("");

  const handleChange = (e) => {
    setValues(e.target.value);
  };

  return (
    <form>
      <h1>검색 시작하기</h1>
      <label htmlFor="location">위치</label>
      <input
        id="location"
        name="location"
        value={values}
        placeholder="어디로 여행가세요?"
        onChange={handleChange}
      />
      <button type="submit">검색</button>
    </form>
  );
}
```

---

### 비제어 컴포넌트

- 인풋 태그의 value 속성을 리액트에서 지정하지 않고 사용하는 컴포넌트이다.

```jsx
function TripSearchForm() {
  const onSubmit = (e) => {
    // 기본 submit 동작 막기
    e.preventDefault();

    const form = e.target;
    const location = form["location"].value;
  };

  return (
    <form onSubmit={onSubmit}>
      <h1>검색 시작하기</h1>
      <label htmlFor="location">위치</label>
      <input id="location" name="location" placeholder="어디로 여행가세요?" />
      <button type="submit">검색</button>
    </form>
  );
}
```

- 참고로 위처럼 작성해도 `onSubmit` 함수에서는 폼 태그를 참조할 수 있다.
- 하지만 비제어 컴포넌트는 값이 실시간으로 동기화 되지 않는다.  
  만약 a와 b라는 컴포넌트가 있을 때, a에 대한 변화를 즉각적으로 b가 영향을 받아야 할때 비제어 컴포넌트는 이런 방식에 대한 대응을 할 수 없는 것이 단점이다.

---

만약 이렇게 제어 컴포넌트랑 비제어 컴포넌트 모두 쓸 수 있는 경우라면

**제어 컴포넌트를 사용하는 것이 좋다!**
