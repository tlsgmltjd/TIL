## CallBack

> 다른 함수의 인자로 전달되는 함수

```js
function main(x) {
  x();
}

function sayHi() {
  console.log("안녕");
}

main(sayHi);
```

---

> 함수를 인자로 전달할 때 () 괄호를 붙히면 안됨.

> 이렇게 되면 sayHi 함수를 전달하는 것이 아닌 리턴값을 전달하게 됨 + 바로 실행됨

```js
main(sayHi()); // 안됨
```

---

> 함수를 인자로 바로 전달할 때 함수 이름을 지우거나 화살표 함수를 사용하여 간결하게 표현 가능

```js
function main(x) {
  x();
}

main(function () {
  console.log("안녕");
});
// or
main(() => {
  console.log("안녕");
});
```

---

> 콜백 함수를 사용하면 마치 부품을 갈아 끼우는것 처럼 함수의 인자를 원하는 콜백함수로 교체하면서 다른 기능을 할 수 있게 해줌

> 콜백함수는 콜백함수를 실행한 함수에 의해서 호출이 되기 때문에 함수 내부 구현사항에서 원하는 시간에 함수를 실행할 수 있음

```js
function greetToUser(greet) {
  const name = "진헌";
  greet(name);
}

function greetInKorean(name) {
  console.log(name + "님, 안녕하세요");
}

function greetInEnglish(name) {
  console.log(name + ", HI!");
}

greetToUser(greetInEnglish);
```

---

### setTimeout()

```js
setTimeout(function () {
  console.log("hi");
}, 1000);

// 콜백함수, 시간(ms)
```

> 콜백함수의 호출은 setTimeout의 구현사항에 의해서 호출됨
