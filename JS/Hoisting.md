## Hoisting

- 자바스크립트는 **변수나 함수의 선언부분**을 변수의 범위 맨 위로 강제로 끌고가서 가장 먼저 해석한다.
- `let, const var`를 포함한 `함수선언문`등 모든 선언을 호이스팅한다.

> var 키워드는 선언과 함께 undefined로 초기화되어 메모리에 저장되는데

> let, const는 호이스팅이 되지만 초기화 되지 않은 상태로 선언만 메모리에 저장되기 때문에 초기화 되지 않으면 참조 에러를 일으킨다.

> let 키워드로 선언된 변수는 스코프의 시작에서 변수의 선언를 `일시적 사각지대(Temporal Dead Zone; TDZ)`라고 부른다.

---

### var 변수의 호이스팅

```js
console.log(name);
var name = "Lee";
console.log(name);
```

`출력`

```
undefined
Lee
```

> 실제 동작

```js
var name;
console.log(name);
name = "Lee";
console.log(name);
```

---

### 함수선언문의 호이스팅

```js
callMe();
function callMe() {
  let HI = "Hello!";
  console.log(HI);
}
```

`출력`

```
Hello!
```

> 실제 동작

```js
function callMe() {
  let HI = "Hello!";
  console.log(HI);
}
callMe();
```
