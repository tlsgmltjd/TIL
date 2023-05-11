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
