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

- rest **객체, 배열, 함수의 매개변수**에서 사용가능하며 spread와 비슷하나 역할이 다르다

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

---

## 구조 분해 할당 (Destructuring assignment)

- 구조 분해 할당 구문은 배열이나 객체의 속성을 해체하여 그 값을 각각 변수에 담을 수 있게 하는 표현식이다.

### 배열

```js
let [firstName, surname] = ["HI"];

alert(firstName); // HI
alert(surname); // undefined
```

- 할당하고자 하는 변수의 개수가 분해하고자 하는 배열의 길이보다 크다면 `undefined`

`=`을 사용하여 기본값을 나타낼 수 있음

```js
let [name = "a", age = 12] = ["b"];

alert(name); // b
alert(surname); // 12 (기본값)
```

### 객체

```js
let Player = {
  name: "Me",
  age: 17,
  height: 177,
};

let { height, name, age } = Player;

alert(name); // Me
alert(age); // 17
alert(height); // 177
```

> 참고로 순서는 중요하지 않다.

---

## try ... catch문

- 예외를 처리하기 위한 구문

```js
try {
  // 예외가 발생할 가능성이 있는 문장
} catch (err) {
  alert("에러 발생");
}
```

- 예외가 발생할 경우 `try -> catch`

### 에러 객체

- `name`: 에러이름

- `message`: error에 대한 상세 내용

### throw

- try문 안에서 throw문를 실행하면 catch 문을 실행할 수 있다.

* JS의 에러 생성자

```js
let error = new Error(message);

let error = new SyntaxError(message);
let error = new ReferenceError(message);
```

```js
try {
  throw new Error("에러 메세지");
} catch (err) {
  alert(err); // Error: 에러 메세지
}
```

### finally

- 예외 발생여부와 상관없이 무조건적으로 실행되는 코드

```js
try {
  // 예외가 발생할 가능성이 있는 문장
} catch (err) {
  alert(err);
} finally {
  alert("끝");
}
```

- 예외가 발생할 경우 `try -> catch -> finally`
