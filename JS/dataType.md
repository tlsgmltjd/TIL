## dataType

- 자바스크립트의 자료형 (문자, 숫자, array, object 등)은 자료형을 크게 2개로 분류한다.

* **Primitive** & **reference**

### Primitive data type

- 문자, 숫자 자료형들이 대표적인 `primitive data type`이다.

```js
let name = "kim";
let age = 20;
```

- 문자나 숫자 자료형은 문자나 숫자가 변수에 직접 저장된다.

### Reference data type

- Array, Object 자료형은 `reference data type`에 속한다.

- `reference data type`은 자료를 변수에 직접 저장하는게 아닌,  
  **자료가 저쪽에 있습니다** 라는 **화살표** (레퍼런스)를 변수에 저장한다.

```js
let human = { name: "Kim" };
```

- Kim이라는 데이터가 변수에 저장된게 아니다.  
  _Kim이라는게 저기 있습니다~_ 라는 정보(화살표)만 저장된다.

### 재미있는 예제

### #1

```js
let 이름1 = { name: "김" };
let 이름2 = { name: "김" };
```

```
이름1 == 이름2
```

`false`가 나온다.

<br />

등호로 비교하고 있는건 `object` 두개가 아니라 `화살표` 두개이다.

![사진](https://codingapple.com/wp-content/uploads/2020/03/%EC%BA%A1%EC%B2%983-1.png)

### #2

```js
let 이름1 = { name: "김" };

function 변경(obj) {
  obj = { name: "park" };
}

변경(이름1);

console.log(이름1);
```

- 변경되지 않고 `{ name: "김" }` 가 나온다.
