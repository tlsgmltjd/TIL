## Promise

- `프로미스`는 자바스크립트 **비동기 처리에 사용되는 객체**이다.

```js
const myPromise = new Promise(function (resolve, reject) { ... });

myPromise.then(() => {}).catch(() => {});
```

> 프로미스 안의 코드가 실행이 **완료**가 되었을 때 `then()` 함수 내의 코드를 실행 시킨다.

> 코드가 실행이 **실패**했을 경우엔 `catch()` 함수 내의 코드를 실행 시킨다.

---

### Promise는 성공 & 실패 판정기

```js
const myPromise = new Promise(function (resolve, reject) {
  resolve("성공!");

  // resolve() : Promise 성공 판정
  // reject() : Promise 실패 판정
});

myPromise
  .then((response) => {
    console.log(response);
  })
  .catch(() => {});
```

> 연산 결과 같은걸 `.then()` 안에서 사용하려면 `resolve()` 함수의 파라미터로 넘겨주면 된다.

---

### Promise 특징

#### Promise의 상태

- **Pending**(대기): 초기 상태로 이행도 실패도 되지 않은 상태

- **fullfiled**(이행): 비동기 처리가 성공적으로 완료된 상태

- **rejected**(실패): 비동기 처리가 실패한 상태

#### Promise는 동기를 비동기로 만들어주는 코드가 아니다.

- Promise는 비동기적 실행과 전혀 상관이 없다.

---

> Coding-Test

```js
const helloPromise = new Promise(function (resovled, rejected) {
  $.get("https://codingapple1.github.io/hello.txt").done((res) => {
    resovled(res);
  });
});

helloPromise.then((res) => {
  const hello2Promise = new Promise(function (resovled, rejected) {
    $.get("https://codingapple1.github.io/hello2.txt")
      .done((res) => {
        resovled(res);
      })
      .then((res) => {
        console.log(res);
      });
  });

  return hello2Promise;
});
```
