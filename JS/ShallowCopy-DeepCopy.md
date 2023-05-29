#### 자바스크립트의 참조 타입의 복사 방법

- 참조 타입(함수, 객체, 배열)의 데이터는 복사 시 데이터의 값이 아닌 '**값이 저장된 메모리의 주소**'가 저장된다.

* 따라서 참조 타입의 복사 방법은 **얕은 복사(Shallow Copy)** 와 **깊은 복사(deep copy)** 로 나뉜다.  
  <br />
* **얕은 복사**: 참조 타입의 데어터의 **메모리 주소 값**

* **깊은 복사** : 새로운 메모리 공간을 차지하고 **완전히 복사**

---

### 얕은 복사(Shallow Copy)

- 객체를 복사할 때 원본 값과 복사된 값이 같은 메모리 주소를 가리키는걸 말한다.

> 객체안에 객체가 있는 경우 한개의 객체라도 원본 객체를 참조한다면 얕은 복사이다.

### Object.assign()

- 메소드 첫번째 인자로 객체를 넣어주게 되면 그 객체에 추가로 더해진 객체가 생성된다.

```js
const jinheon = { a: 1 };
const yisung = Object.assign({}, jinheon);

newObj.a = 2;

console.log(jinheon); // { a: 1 }
console.log(jinheon === yisung); // false
```

하지만 Object.assign()를 사용하면 완전하게 깊은 복사가 되지는 않는다.

- Object.assign()를 사용하면 객체 자체는 깊은 복사가 수행되지만 **2차원 이상의 객체는 얕은 복사**가 수행된다.

```js
let jinheon = {
  a: 1,
  b: {
    c: 2,
  },
};

let copy = Object.assign({}, jinheon);
copy.b.c = 3;

console.log(jinheon ==== copy); // fasle
console.log(jinheon.b.c ==== copy.b.c); // true
```

객체 자체는 서로 다른 주소를 참조하고 있어 깊은 복사가 수행되지만  
내부 객체는 같은 주소를 참조하고있다.

### Spread

Spread 구문도 복사한 객체는 깊은 복사지만 내부 객체는 얕은 복사가 이루어진걸 볼 수 있다.

```js
const obj = {
  a: 1,
  b: {
    c: 2,
  },
};

const newObj = { ...obj };

newObj.b.c = 3;

console.log(obj === newObj); // false 깊은 복사?
console.log(obj.b.c === newObj.b.c); // true 내부 객체는 얕은 복사
```

---

### 깊은 복사(Deep Copy)

- 깊은 복사된 객체 안에 객체가 있을 경우에도 **원본과의 참조가 완전히 끊어진** 객체

### JSON 객체

JSON 객체의 **parse와 stringify**를 이용해서 깊은 복사를 할 수 있다.  
단점 : 느림, 객체가 함수일 경우 -> `undefined`

```js
const jinheon = {
  a: 1,
  b: {
    c: 2,
  },
};

const origin = JSON.parse(JSON.stringify(jinheon));

origin.b.c = 3;

console.log(jinheon.b.c === origin.b.c); // false
```

> 추가로 재귀 함수를 이용하여 깊은 복사 function을 만들어 이용하는 방법도 있다.
