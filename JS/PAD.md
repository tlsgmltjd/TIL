## PAD

> 좌우에 특정한 문자열로 채우는 기능

### .padStart() / .padEnd()

> string.padStart(maxLength, fillString);  
> string.padEnd(maxLength, fillString);

- 첫번째 파라미터로 maxLength를 받아 문자열의 길이가 maxLength보다 작을 경우 나머지를 두번째 파라미터로 받은 문자열로 채워주는 기능

```js
const hours = "12";
const minutes = "5";
const seconds = "8";

console.log(hours.padStart(2, "0"));
console.log(minutes.padStart(2, "0"));
console.log(seconds.padStart(2, "0"));
```

> 12 05 08
