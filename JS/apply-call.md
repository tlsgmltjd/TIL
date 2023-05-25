## apply, call

### apply

```js
let person = {
  인사: function () {
    console.log(this.name + "안녕");
  },
};

let person2 = {
  name: "손흥민",
};

person.인사.apply(person2);

// 손흥민 안녕
```

> person.인사()를 실행할 때 person2 오브젝트에 적용하여 실행하라는 뜻

<br />

```js
let person2 = {
  name: "손흥민",
  인사: function () {
    console.log(this.name + "안녕");
  },
};

person2.인사(); // 이렇게 실행된 느낌
```

---

### call

> 차이점 : 파라미터 전달 방식

```js
let person = {
  인사: function () {
    console.log(this.name + "안녕");
  },
};

let person2 = {
  name: "손흥민",
};

person.인사.apply(person2, [1, 2, 3]); // 파라미터를 [array]로 한꺼번에 집어넣을 수 있다
person.인사.call(person2, 1, 2, 3); // 일반 함수처럼만 집어넣을 수 있다.
```

```js
function 더하기(a, b, c) {
  console.log(a + b + c);
}

let array = [10, 20, 30];

더하기.apply(undefined, array); // 함수 파라미터에 array 값을 넣기
```

> apply를 사용하여 함수 파라미터에 array 값을 넣을 수 있지만..

<br />
<br />

```js
더하기(...array);
```

> Spread 문법을 사용하여 쉽게 표현 가능
