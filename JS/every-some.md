## every / some

### every 메소드

- `every`는 배열을 반복하면서 모든 요소가 콜백함수가 리턴하는 조건을 만족한다면. `true`  
  만족하지 않는 요소가 등장한다면 바로 `false`를 리턴하고 종료된다.

```js
const numbers = [1, 2, 3, 4, 5];

const everyReturn = numbers.every((element) => {
  return element > 5;
});

console.log(everyReturn); // false
```

### some 메소드

- 배열을 반복하면서 모든 요소가 콜백함수가 리턴하는 조건을 만족하지 않는다면 `false`를 리턴하고, **배열을 반복하면서 콜백함수가 리턴하는 조건을 만족하는 요소가 등장한다면** 바로 `true`를 리턴하고 반복을 종료

```js
const numbers = [1, 2, 3, 4, 5, 6];

// some: 조건을 만족하는 요소가 1개 이상 있는지
const someReturn = numbers.some((element) => {
  return element > 5;
});

console.log(someReturn); // true;
```
