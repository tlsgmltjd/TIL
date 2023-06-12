## async await

- `async`를 사용하면 `promise` 코드를 훨씬 직관적으로 나타낼 수 있는 장점이 있다.

* 그리고 함수 앞에 `async` 키워드만 붙히면 함수 자체가 `Promise` 가 된다.

- `async` 함수의 `return`값은 `resolve()` 의 파라미터의 값과 같다.

> Promise

```js
const addtionPromise = new Promise((resolved, rejected) => {
  resolved(1 + 1);
});

addtionPromise.then((response) => {
  console.log("더하기 성공했어요 : " + response);
});
```

> async

```js
async function Addtion() {
  return 1 + 1;
}

Addtion().then((response) => {
  console.log("더하기 성공했어요 : " + response);
});
```

---

### .then() -> await

- `await` 키워드는 `async` 키워드를 붙힌 함수에서만 사용이 가능하다.

* `await`는 `Promise`가 완료될 때까지 기다린다.

- `await`는 `Promise`가 `resolve`한 값을 내놓는다.

```js
async function Addtion() {
  const veryVeryHardCalculation = new Promise((resolved, rejected) => {
    const result = 1 + 1;
    resolved(result);
  });

  const result = await veryVeryHardCalculation;
}

Addtion();
```

`const result = await veryVeryHardCalculation`

- `veryVeryHardCalculation Promise`를 기다린 다음에 완료되면 결과를 `result`에 담아주세요~ 라는 뜻 이다.

---

### async 예외처리

```js
async function Addtion() {
  const veryVeryHardCalculation = new Promise((resolved, rejected) => {
    rejected();
  });

  const result = await veryVeryHardCalculation;
}

Addtion();
```

- 이렇게 `Promise` 가 실패해버리면 `await veryVeryHardCalculation;` 코드는 에러가 나고 코드 실행이 멈춰버린다!.

#### 이럴땐 try .. catch 문을 이용하여 예외 처리를 할 수 있다.

```js
async function Addtion() {
  const veryVeryHardCalculation = new Promise((resolved, rejected) => {
    rejected("실패ㅠ");
  });

  try {
    // 이 코드를 실행!
    const result = await veryVeryHardCalculation;
  } catch (error) {
    // 실패했다면 이 코드를 실행
    console.log(error);
  }
}

Addtion();
```

> `reject`에 에러 메시지를 담을 수 있고, `catch(error) => { console.log(error) }` 이렇게 출력할 수 있다.
