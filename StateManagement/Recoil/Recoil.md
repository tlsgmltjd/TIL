## Recoil ⌘

```
npm install recoil
```

### Recoil의 특징

- 각각 전역 상태에 대한 `atom`을 생성하여 구성 요소만 리렌더링 된다. (불필요한 렌더링 방지)

---

## Atoms

- `Atoms`는 상태 단위이며, 업데이트와 참조가 가능하다.
- atom이 업데이트되면 각각의 컴포넌트들은 리렌더링 된다!

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
