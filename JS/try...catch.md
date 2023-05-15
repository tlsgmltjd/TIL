## try ... catch문

- 예외를 처리하기 위한 구문

```js
try {
  // 예외가 발생할 가능성이 있는 문장
} catch (err) {
  alert("에러 발생");
}
```

- 예외가 발생할 경우 `try -> catch`

### 에러 객체

- `name`: 에러이름

- `message`: error에 대한 상세 내용

### throw

- try문 안에서 throw문를 실행하면 catch 문을 실행할 수 있다.

* JS의 에러 생성자

```js
let error = new Error(message);

let error = new SyntaxError(message);
let error = new ReferenceError(message);
```

```js
try {
  throw new Error("에러 메세지");
} catch (err) {
  alert(err); // Error: 에러 메세지
}
```

### finally

- 예외 발생여부와 상관없이 무조건적으로 실행되는 코드

```js
try {
  // 예외가 발생할 가능성이 있는 문장
} catch (err) {
  alert(err);
} finally {
  alert("끝");
}
```

- 예외가 발생할 경우 `try -> catch -> finally`
