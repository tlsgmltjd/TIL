## prototype

> 상속

```js
function Students() {
  this.name = "Kim";
  this.age = 15;
}

let Student1 = new Students();
let Student2 = new Students();

console.log(Students.prototype);
```

- `constructor`를 만든다면 `prototype` 이라는 항목이 생성된다.

<br />

```js
function Students() {
  this.name = "Kim";
  this.age = 15;
}

Students.prototype.gender = "Male";

let Student1 = new Students();
let Student2 = new Students();

console.log(Student1.gender);
console.log(Student2.gender);

// Male
// Male
```

- `constructor` 의 `prototype`에 `gender: "Male"` 이라는 데이터를 추가한 것이다.
- 이렇게 `Student1`, `Student2` 같은 `constructor`로 생성되는 모든 자식들은 `gender` 이라는 속성을 가진다.

---

```js
function Students() {
  this.name = "Kim";
  this.age = 15;
}

Students.prototype.gender = "Male";

let Student1 = new Students();
let Student2 = new Students();

console.log(Student1.gender);

// Male
```

- `Male` 이 출력되는 이유는?

#### 자바스크립트에서 오브젝트의 값을 출력하는 순서

1. Student1에 직접 gender라는 값이 있는가?

2. 그럼 부모 `prototype`에 gender라는 값이 있는가?

3. 그럼 부모의 부모 `prototype`에 gender라는 값이 있는가?

4. 그럼 부모의 부모의 부모의 `prototype`에 .. 그게 있는가?

`내가 직접 가지고 있는지 검사` -> `내가 가지고 있지 않으면 부모 prototype들을 차례로 검사`

---

### `__proto__`

- 부모로부터 생성된 자식 object들은 `__proto__`라는 속성이 있다
- `__proto__`는 **부모의 `prototype`** 이다

```js
function Students() {
  this.name = "Kim";
  this.age = 15;
}

Students.prototype.gender = "Male";

let Student1 = new Students();

console.log(Student1.__proto__);
console.log(Students.prototype);

// {gender: 'Male', constructor: ƒ}
// {gender: 'Male', constructor: ƒ}
```

- `__proto__`는 `부모 prototype`을 의미

---

### 자바스크립트 내장함수를 사용할 수 있는 원리

```js
let arr = [1, 2, 3];
console.log(arr.toString());
```

- 이렇게 사용할 수 있는건 `arr` 변수의 부모의 `prototype`가 toString() 를 가지고 있기 때문이다.

<br />

```js
let arr = [1, 2, 3];
```

- 일반적으로 배열은 이렇게 만든다.

=

```js
let arr = new Array(1, 2, 3);
```

- 하지만 내부적으로는 저렇게 new 키워드를 항상 이용해서 array/object를 만들어준다.

* `new` `Array` 라는 뜻은, `Array`라는 `constructor`로 자식을 하나 뽑아준다는 뜻이다.
* 그래서 `Array`로부터 생성된 자식들은 `Array`의 `prototype`에 부여되어있는 함수, 데이터들을 사용가능하다.

---

### prototype으로 상속시키는거랑 constructor로 상속시키는 것의 차이?

- 자식들이 값을 직접 소유하게 만들고 싶으면 `constructor`로 상속

- 부모만 가지고 있고 그걸 참조해서 쓰게 만들고 싶으면 `prototype`으로 상속
