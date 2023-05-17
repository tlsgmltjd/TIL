## ArrayFunction

## forEach()

```js
const Array = ["국어", "수학", "영어", "과학"];
arr.forEach((item) => console.log(item));
```

- **forEach()** 메소드는 각 요소들을 인자로 받아와  
  콜백 함수 내부에서 주어진 함수를 배열 각각의 요소를 넣어 실행

---

## map()

```js
const Array = [1, 2, 3, 4, 5, 6, 7, 8];
arr.map((num) => num * 2);
// [2, 4, 6, 8, 10, 12, 14, 16]
```

- **map()** 메소드는 배열의 각 요소에 대해 주어진 함수를 호출한 결과를 **새로운 배열로 반환한다**.
  > 원본 배열을 변하지 않으며 새로운 배열을 생성하는데 사용한다.

---

## filter()

```js
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter((num) => {
  return num % 2 === 0;
});
console.log(evenNumbers);
// 출력: [2, 4]
```

- 주어진 함수의 반환값이 true인 요소로 이루어진 새로운 배열을 반환한다.
  > 원본 배열은 변경되지 않으며 특정 조건에 맞는 요소들을 필터링하는데 사용한다.

---

## sort()

```js
const fruits = ["banana", "apple", "orange", "grape"];
const sortedFruits = fruits.sort();
console.log(sortedFruits);
// 출력: ['apple', 'banana', 'grape', 'orange']
```

- 배열의 요소를 정렬한다.

+) _내용추가_ _정렬기능_

---

## reduce()

```js
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((accumulator, num) => {
  return accumulator + num;
}, 0);
console.log(sum);
// 출력: 15
```

- 배열의 각 요소에 대해 주어진 함수를 실행하고, 하나의 값을 축적하여 반환한다.
