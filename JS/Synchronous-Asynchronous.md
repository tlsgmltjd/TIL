## 동기 / 비동기

![](https://codingapple.com/wp-content/uploads/2020/04/271c176806330.jpeg)

![](https://velog.velcdn.com/images/dlrkdals227/post/8b3d9a1f-754d-4670-969f-710ebc4c250d/image.png)

자바스크립트에서는 거의 대부분의 작업들이 **비동기**로 이루어진다.

> 자바스크립트는 동기방식 언어이다.

- **비동기 처리**란 특정 코드의 연산이 끝날 때까지 코드의 실행을 멈추지 않고,다음 코드를 먼저 실행하는 처리 방식이다.

### setTimeout 메서드

- setTimeout()은 가장 대표적인 비동기 함수이다.

```js
setTimeout(() => console.log("음"), 1000);
console.log("엥");

// 엥
// ... 1000ms
// 음
```

자바스크립트를 실행해주는 `웹브라우저`는

이런 특수한 코드들`(ex. setTimeOut())`을 발견하면 약간 제쳐두고(Queue) 다른 코드부터 실행한다!

- 이런 처리방식이 **비동기** 이다.

### 콜백함수

자바스크립트에 `비동기 상황` 등에서 코드를 순차적으로 실행할 때 `콜백함수`를 사용한다.

```js
function firstFunction() {
  console.log(1);
}

function secoundFunction() {
  console.log(2);
}

firstFunction();
secoundFunction();
```

> 자바스크립트는 비동기라는 특수성으로 인해 이렇게 쓴다고 순차적으로 실행하는걸 보장하진 않는다!

```js
function firstFunction(callBackFunction) {
  console.log(1);
  callBackFunction();
}

function secoundFunction() {
  console.log(2);
}

firstFunction(secoundFunction);
```

> 콜백함수 디자인
