## Slice Splice Split

> Array method: Slice() / Splice()  
> String method: Split()

---

### Slice()

- slice()는 배열 메서드로 원하는 부분을 **새로운 배열**로 리턴한다.

> 기존 배열 변경 ❌

```js
let arr = ["A", "B", "C", "D", "E", "F"];
newArr = arr.slice(2, 5);
// ["C", "D", "E"]
```

### Splice()

- Splice() 또한 배열 메서드로 **배열에 원하는 요소를 추가**하거나 **제거**할 수 있다.

> 기존 배열에 변화를 준다!!

```js
let arr = ["A", "B", "C", "D", "E", "F"];
newArr = arr.splice(1, 3);
// ["B", "C", "D"]
```

```js
let arr = ["A", "B", "C", "D", "E", "F"];
newArr = arr.splice(1, 3, "HI", "HI", "HI");
console.log(arr);
// ['A', 'HI', 'HI', 'HI', 'E', 'F']
```

### Split()

- Split()은 string 메서드지만 배열을 리턴한다.

* **문자열을 잘라서 배열에 담을 때 유용하다.**

```js
const str = "a/b/c";
const arr = str.split("/");
console.log(arr);
// ['a', 'b', 'c']
```

```js
SetID(response.data?.email.split("@")[0]);
```

> 실제 사용  
> 이메일의 `'@'` 기호 앞의 사용자의 아이디를 저장할 때
