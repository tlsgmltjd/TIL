## useTabs

```jsx
import { useState } from "react";

export function useTabs(initialTab, allTabs) {
  const [currentIndex, setCurrentIndex] = useState(initialTab); // 0

  if (!allTabs || !Array.isArray(allTabs)) {
    return;
  }

  return {
    currentItem: allTabs[currentIndex],
    changeItem: setCurrentIndex,
  };
}
```

> `useTabs(초기 탭, 모든 탭 데이터)`

```jsx
// test 용 Mock 데이터
const content = [
  {
    tab: "Section 1",
    content: "This is Section 1",
  },
  {
    tab: "Section 2",
    content: "This is Section 2",
  },
];

function App() {
  // useTabs 훅을 사용한다.
  // 초기 탭 위치는 0, 모든 탭 데이터를 넘겨준다.
  const { currentItem, changeItem } = useTabs(0, content);

  return (
    <div>
      {content.map((section, index) => (
        <button
          onClick={() => {
            changeItem(index);
          }}
        >
          {section.tab}
        </button>
      ))}
      <div>{currentItem.content}</div>
    </div>
  );
}
```

---

```json
const content = [
  {
    tab: "Section 1",
    content: "This is Section 1",
  },
  {
    tab: "Section 2",
    content: "This is Section 2",
  },
];
```

> test 용 데이터는 이렇게 생겼다.

- App 컴포넌트에서 데이터에 .map() 메서드를 사용하여 버튼을 그려준다.
- 각각의 버튼은 `[Section 1]`, `[Section 2]` 이렇게 생겼고 `0`, `1` 이라는 index 를 가진다.
- 버튼을 눌렀을 때 `useTabs()` 훅에서 리턴받은 `changeItem()` 함수에 `index` 값을 전달한다.
- 아래에는 `useTabs()` 훅에서 리턴받은 `currentItem` 의 `content` 를 출력한다.

<br />

- `useTabs(initialTab, allTabs)` 훅은 `초기탭의 위치`, `모든 탭 데이터` 를 파라미터로 받는다.

```jsx
export function useTabs(initialTab, allTabs) {
  const [currentIndex, setCurrentIndex] = useState(initialTab); // 0

  if (!allTabs || !Array.isArray(allTabs)) {
    return;
  }

  return {
    currentItem: allTabs[currentIndex],
    changeItem: setCurrentIndex,
  };
}
```

- `currentIndex` 스테이트에 초기 탭 위치로 초기화 시키고
- **탭이 있는지?** **배열인지?** 를 한 번 검사한다.

* `useTabs()`훅은 객체를 리턴한다.

```js
{
    currentItem: allTabs[currentIndex],
    changeItem: setCurrentIndex,
}
```

- `currentItem` : 현제 탭의 데이터 (ex. {
  tab: "Section 1",
  content: "This is Section 1",
  })
- `changeItem` : 탭의 위치를 변경할 때 (ex. 0, 1)
