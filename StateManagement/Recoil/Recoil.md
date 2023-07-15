## Recoil ⌘

ref : https://wit.nts-corp.com/2022/10/13/6586

```
npm install recoil
```

### Recoil의 특징

- 각각 전역 상태에 대한 `atom`을 생성하여 구성 요소만 리렌더링 된다. (불필요한 렌더링 방지)

---

## RecoilRoot

- 컴포넌트에서 Recoil state를 사용하기 위해서는 recoil 상태를 사용하고자 하는 컴포넌트의 부모에 `RecoilRoot`를 선언해주어야한다.

```js
import { RecoilRoot } from "recoil";

const App = () => {
  return (
    <RecoilRoot>
      <Routers />
    </RecoilRoot>
  );
};
```

## Atoms

- `Atoms`는 상태 단위이며, 업데이트와 참조가 가능하다.
- atom이 업데이트되면 각각의 컴포넌트들은 리렌더링 된다!

```js
atom({ key: "", default: "" });
```

> key : atom을 식별하는데 사용하는 전역적으로 고유한 문자열  
> default : atom의 초기값

```ts
import { atom } from "recoil";

export const userName = atom({
  key: "Name", // 고유한 키 값
  default: "Shin",
});
```

### atom의 값을 가져올 때

> useRecoilValue

```js
import { useRecoilValue } from "recoil";
import { userName } from "../atoms";

const userName = useRecoilValue(userName);

console.log(userName);
// Shin
```

### atom의 값을 수정할 때

> useSetRecoilState

```js
import { useSetRecoilState } from "recoil";
import { userName } from "../atoms";

const setUserName = useSetRecoilState(userName);

setUserName("Lee");
```

### 둘 다

> useRecoilState

```js
import { useRecoilState } from "recoil";
import { userName } from "../atoms";

const [userName, setUserName] = useRecoilState(userName);

setUserName("Lee");

console.log(userName);
// Lee
```

## seletors

- 전역 상태 값을 기반으로 어떤 계산을 통해 새로운 값을 내뱉는 순수함수이다.
- atom이나 다른 selector를 통해 입력을 받을 수 있다.

## get

- `get` 매개변수를 이용하여 **atom이나 다른 selector를 참조할 수 있다.**

```js
export const countNextState = atom({
  key: "count",
  default: 0,
});

// selector
export const countNextSeletor = selector({
  key: "toDoSelector",
  get: ({ get }) => {
    const count = get(countNextState);

    return count + 1;
  },
});
```

- `useRecoilValue()` hook을 사용해서 seletor의 값을 읽을 수 있다.

```js
const App = () => {
  const nextCount = useRecoilValue(countNextSeletor);

  return <div>next number is : {nextCount}</div>;
};
```

## set

- `set` 함수를 통해 selector는 **쓰기 가능한** RecoilState 객체를 반환 한다.

- set 함수는 원하는 atom을 지정하여 수정할 수 있게 해준다.

```js
import { atom, selector } from "recoil";

export const minutesState = atom({
  key: "minutes",
  default: 0,
});

export const hourSelector =
  selector <
  number >
  {
    key: "hours",
    get: ({ get }) => {
      const minutes = get(minutesState);
      return minutes / 60;
    },
    set: ({ set }, newValue) => {
      const minutes = +newValue * 60;
      set(minutesState, minutes);
    },
  };
```

- 두번째 argument는 값에 적용시킬 새로운 값이다.

```js
const [hours, setHours] = useRecoilState(hourSelector);

const onHoursChange = (event: React.FormEvent<HTMLInputElement>) => {
  setHours(+event.currentTarget.value);
};
```
