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
