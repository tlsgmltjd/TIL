# JS

- JS 란 웹페이지에서 사용하기 위해 만든 언어

* **객체기반 언어**이며, HTML 문서 내에 내장되어 프로그래밍 요소를 추가할 수 있다.
* 거의 모든 웹 브라우저가 JS 엔진을 내장하고 있기 때문에 JS 코드를 해석하고 실행할 수 있다.

---

## 기본 문법

#### 변수

```js
let 변수이름;
const 변수이름: // 상수 선언
```

#### 함수

```js
function 함수이름(파라미터) {
  console.log("콘솔출력" + 파라미터);
}

함수이름(파라미터);
```

#### if문

```js
if (조건) {
} else if (조건) {
} else {
}
```

#### switch문

```js
switch (비교할 값) {
case 조건값1:
동작부분;
break;
case 조건값2:
동작부분;
break;
default:
동작부분;
}
```

#### for 문

```js
for (초기화 부분; 조건 부분; 추가동작부분) {

}

for (let i = 1; i <= 10; t++) {

}
```

#### while 문

```js
while (조건부분) {}
```

```js
continue; // 반복문 넘너뜀
```

#### 객체

```js
객체;
let id = {
  brandName: "신희성",
  bornYear: 2007,
};

// 점 표기법
console.log(id.brandName); // 신희성

// 대괄호 표기법
console.log(id["brandName"]); // 신희성
```

```js
let id = {
  name: "신희성",
  age: 17,
};

console.log(id.name); // 출력
id.name = "시니성"; // 프로퍼티 수정
id.major = "developer"; // 프로퍼티 추가
delete id.name; // 프로퍼티 삭제

// "프로퍼티이름" in object
console.log("name" in id); // 프로퍼티 존재여부 확인
```

```js
// 메소드
let greet = {
  sayHello: function () {
    console.log("Hello");
  },
  sayHi: function () {
    console.log("Hi");
  },
};

greet.sayHello();
```

#### for .. in 문

```js
// for .. in
/_
for (변수 in 객체) {
동작
}
_/

let id = {
name: 'aaa',
age: 15
}

for (let i in id) {
console.log(i);
}
```

#### Date 객체

```js
// Date
let myDate = new Date();
console.log(myDate);
console.log(myDate.getDay());

// month 값은 0부터 시작 (0 > 1월)
let birthDay = new Date(2023, 02, 01, 10, 10, 10);
console.log(birthDay);

console.log(birthDay.getTime());
```

#### 배열

```js
// 배열
let coursRank = ["A", "B", "C"];

// indexing (0 ~ …)
console.log(coursRank[0]);
```

#### splice();

```js
let members = ["a", "b", "c", "d", "e"];

// 배열 요소 삭제

// splice (인덱스, [삭제할개수], [추가할값]);
members.splice(1, 1, "HELLO WORLD");
console.log(members);
```

#### shift(), pop(), unshift(), push()

```js
let members = ["a", "b", "c", "d", "e"];

// 배열의 첫 요소를 삭제: shift()
members.shift();
console.log(members);

// 배열의 마지막 요소를 삭제: pop()
members.pop();
console.log(members);

// 배열의 첫 요소로 값 추가: unshift(추가할 값)
members.unshift("A");
console.log(members);

// 배열의 마지막 요소로 값 추가: push(추가할 값)
members.push("E");
console.log(members);
```

```js
(배열 매소드들)
특정 값 찾기 .indexOf() / .lastIndexOf()

특정 값이 있는지 확인하기 .includes()

배열 뒤집기 .reverse()
```

#### 배열 반복문- for ... of

```js
// for ... of
let phone = ["Apple", "Samsung", "Lg"];

// for (변수 of 배열)
for (let i of phone) {
  console.log(i);
}
```

#### Mate() 객체

```js
// Mate() 객체

// .abs 절댓값
console.log(Math.abs(-10));

// .max , .min 최댓값 , 최솟값
console.log(Math.max(2, 1, 0));
console.log(Math.min(2, 1, 0));

// .pow 거듭제곱
console.log(Math.pow(2, 3));

// .sqrt 제곱근
console.log(Math.sqrt(49));

// .round 반올린
console.log(Math.round(2.7));

// .floor / .ceil 버림, 올림
console.log(Math.floor(2.4));
console.log(Math.ceil(2.8));

// .random 난수 (0 이상 1 미만)
console.log(Math.random());
```

#### 변수의 기본형과 참조형

```js
// 기본형 Number String Boolean Null undefined / 변수 = 값
// 참조형 Objecct / 변수 = 주소

let x = { name: "신희성" };
let y = x; // x 값에는 주소값이 있기 때문에 y변수에 객체 주소를 복사

console.log(x);
console.log(y);

y.birth = 070301; // x와 y는 주소값이 할당되어있음 수정해도 값이 같음

console.log(x);
console.log(y);
```

#### 참조형 주의

```js
let ob1 = [1, 2, 3, 4, 5];
let ob2 = ob1.slice();
// 배열 ob2에 배열 ob1를 그냥 할당시키면 주소값이 복사되어
// 한쪽 변수를 수정 시 두 변수 모두 가리키는 배열(오브젝트(참조형))이 같음으로
// 값이 같기 때문에 .slice() 를 사용하여 ob2 값에 ob1 값을 복사.

ob2.push(5, 6, 7, 8);

console.log(ob1);
console.log(ob2);
```

---

```js
// 형 변환

// String, Number, Boolean
console.log(Number("10"));
console.log(String(10));

// false (faisy 값)
console.log(Boolean(""));
console.log(Boolean(NaN));
console.log(Boolean(0));
```

```js
console.log(4 + "2"); // 42(string)
```

#### '==' ? '==='

```js
console.log(1 === "1"); // 일치, 불일치(!==)
console.log(1 === true);
console.log(1 == "1"); // 동등, 부등(!=) / 형변환됨
console.log(1 == true);
```

```js
let year = 2023;
let month = 3;
let day = 15;

console.log(`${year}년 ${month}월 ${day}일`); // 백틱 이용 ``
console.log(null === undefined);
console.log(null == undefined);
```

```js
// null : 의도적
console.log(null === undefined); // false
console.log(null == undefined); // true
```

<br />
<br />
<br />
<br />

---

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

---

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

---

<br />
<br />

#### toggle

```js
function handleTitleClick() {
  const clickedClass = "active";
  h1.classList.toggle(clickedClass);
}
```

> handleTitleClick 함수가 실행 되었을 떄  
> h1의 class에 `active` 가 없다면 추가, 있다면 삭제한다! (말 그대로 토글 기능)

---

<br />
<br />
