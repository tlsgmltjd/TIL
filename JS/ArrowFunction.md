## Arrow function

```js
let PreetyFunctoin = () => {};
```

- function 키워드 대신에 **=>** 이런 예쁜 화살표를 사용해서 함수를 만들 수 있다.

---

### 1. arrow function을 쓰면 입출력기능이 직관적이고 이쁘다.

#### Function 을 사용하는 이유?

1. 여러가지 기능을 하는 코드를 한 단어로 묶고 싶을 때
2. 입출력기능을 만들 때

`input` -> `Function` -> `output`

```js
let 진헌이가두배 = (x) => {
  return x * 2;
};
```

### 2. 소괄호 생략 가능

파라미터가 하나라면 소괄호를 생략가능합니다.

```
let 진헌이가두배 = x => { return x * 2 }
```

### 3. 중괄호 생략 가능

```
let 진헌이가두배 = x => x * 2;
```

---

## Arrow function의 this

- 일반 function

```js
let OBJ = {
  함수: function () {
    console.log(this);
  },
};

OBJ.함수();
```

> 실행결과 : {함수: ƒ}

- Arrow function

```js
let OBJ = {
  함수: () => {
    console.log(this);
  },
};

OBJ.함수();
```

> 실행결과 : window

- arrow function은 **외부에 있던 this를 그대로 내부로 가져와서 사용**하는 함수이다
