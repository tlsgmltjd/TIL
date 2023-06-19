## 배열 렌더링

## map 으로 렌더링하기

- 배열 메소드 `map`에서 콜백 함수의 리턴 값으로 리액트 엘리먼트를 리턴하면 된다.

```jsx
function App() {
  const items = [
    { id: 0, name: "희성", point: 100 },
    { id: 1, name: "미리", point: 200 },
    { id: 2, name: "가온", point: 400 },
    { id: 3, name: "태연", point: 600 },
    { id: 4, name: "예슬", point: 900 },
  ];

  return (
    <ul>
      {items.map((item) => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}
```

#### 반드시 key 를 내려주자

- 각 요소를 렌더링 할 때는 최상위 태그에다가 **고유한**`key` Prop을 내려줘야한다.

---

## sort 로 정렬하기

- 배열 메소드의 `sort` 메소드를 사용하여 배열을 정렬할 수 있다.

```jsx
function App() {
  const items = [
    { id: 0, name: "희성", point: 100 },
    { id: 1, name: "미리", point: 200 },
    { id: 2, name: "가온", point: 400 },
    { id: 3, name: "태연", point: 600 },
    { id: 4, name: "예슬", point: 900 },
  ];

  const sortedItems = items.sort((a, b) => {
    return b.point - a.point;
  });

  return (
    <ul>
      {sortedItems.map((item) => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}
```

- `Point` 프로퍼티가 높은 순서대로 정렬하여 출력한다.
