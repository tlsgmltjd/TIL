## var let const

### 선언

```js
var name; // 재선언 O 재할당 O
let age; // 재선언 X 재할당 O
const gender; // 재선언 X 재할당 X
```

> let , const 는 같은 이름의 변수를 두번 이상 재선언 할 수 없다.

```js
var name;
var name; // 가능

let age;
let age; // ERROR

const gender;
const gender; // ERROR
```

---

### 할당

```js
let name; // 선언!
name = "ShinHuiSeong"; // 할당!
```

> const로 변수를 만들면 나중에 값을 변경(할당하는 것이 안된다.)

```js
var name = "AAA";
name = "BBB"; // 가능

let age = 10;
age = 20; // 가능

const gender = "M";
gender = "B"; // ERROR
```

#### 변경이 가능한 const?

```js
const obj = { name: "Shin" };
obj.name = "Park"; // 이게 됨
```

> 엄밀히 말하면 변수를 재할당 한 것이 아니기 때문에 가능하다.

> 변경 하여도 const로 선언된 obj 오브젝트는 오브젝트 이기 때문에!

> Object.freeze() 라는 JS 기본함수를 사용하여 배열 값 안의 변수도 못 바꾸게 설정 가능하다.

---

### 범위

- #### var 변수의 범위 : function내에서만

```js
function handle() {
  var name = "Shin";
  console.log(name); //가능 (같은 함수 블록 안에 있음)
}

console.log(name); //에러
```

- #### let, const 범위 : {} 중괄호내에서만

```js
if (true) {
  let name = "Shin";
  console.log(name); //가능 (같은 코드 블록 안에 있음)
}

console.log(name); //에러
```
