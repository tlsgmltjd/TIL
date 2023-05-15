## Spread 연산자

- Spread 연산자는 `...` 을 통해 사용할 수 있다.

```js
const arr = [1, 2, 3, 4, 5];

console.log(arr); // [ 1, 2, 3, 4, 5 ]
console.log(...arr); // 1, 2, 3, 4, 5
console.log(1, 2, 3, 4, 5); // 1, 2, 3, 4, 5
```

```js
const a = [1, 2, 3];
const a = [4, 5, 6];

console.log([...a, ...b]); // [ 1, 2, 3, 4, 5, 6 ]
```

- 이렇게 배열을 전개하는 것이 Spread 문법이다.

## Rest 연산자

- rest **객체, 배열, 함수의 매개변수**에서 사용가능하며 spread와 비슷하나 역할이 다르다.

### 객체

```js
const obj = {
  name: "Lee",
  age: "17",
  height: 177,
};
const { height, ...rest } = obj;
console.log(height); // '177'
console.log(rest); // { name:'Lee', age:'17' }
// rest 안에는 height를 제외한 나머지 값
```

> rest의 이름이 꼭 rest일 필요는 없다!

### 배열

```js
const number = [1, 2, 3, 4, 5];
const [first, ...rest] = number;
console.log(first);
// 1
console.log(rest);
// 1을 제외한 나머지 [2, 3 ,4, 5]
```

### ⚠

```js
const number = [1, 2, 3, 4, 5];
const [ ...rest, first ] = number;
```

> rest는 꼭 마지막에만 위치해야함

## 매개변수

- 함수의 매개변수가 **몇 개가 될지 모르는 상황**에서 rest 매개변수를 사용하면 유용

```js
function JINHEON(...rest) {
  return rest;
}
const result = JINHEON(10, 20, 30);
console.log(result); // [10, 20, 30]
```

> 매개변수가 배열 형식으로 들어온다.
