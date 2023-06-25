## Typescript 에서 지정할 수 있는 타입

### 숫자형(Number)

```ts
let value: number = 10;
```

### 문자열(String)

```ts
let value: string = "abc";
```

### 논리형(Boolean)

```ts
let value: boolean = true;
```

### 배열(Array)

```ts
let value: number[] = [1, 2, 3];

let value2: Array<number> = [1, 2, 3];
```

### 객체(Object)

```ts
let value: { name: string; age: number } = { name: "Shin", age: 17 };
```

### 모든 타입(unKnown)

```ts
let value: unknown = 10;
```

---

### 함수에서 타입 지정

```ts
function toSum(a: number, b: number): number {
  return a + b;
}

console.log(toSum(10, 20)); // 30
```

> **매개변수의 타입지정**과 **리턴 값의 타입지정**이 가능하다.

### 반환 값이 없는 함수의 타입 지정

```ts
function toSum(): void {}

console.log(toSum());
```

#### Option

```ts
function toSum(a?: number): void {}

console.log(toSum());
```

> `a` 라는 파라미터가 들어올 수도 있고 안 들어올 수도 있다.

> `(a?: number)` = `(a: number | undefined)`  
> 이 둘은 같다!

### 여러 타입 허용(Union type)

```ts
let value: string | number;

value = "123";
value = 10;
```

**Array & Object 에서 Union type**

```ts
let muArray: (number | string)[] = [1, "2", 3];
let myObject: { data: number | string } = { name: "abc" };
```

---

### readonly

> readonly가 있으면 최초 선언 후 수정 불가

```ts
const People: { readonly name: string } = {
  name: "ABC",
};

People.name = "DEF"; // error
```

### Alias(별칭) 타입

```ts
type Player = {
  name: string;
  age?: number;
};

let Jineon: Player = {
  name: "Jinheon",
  age: 17,
};
```

### 튜플 타입 (Tuple)

> 튜플은 길이와 각 요소마다의 타입이 고정된 배열이다

```ts
type myTuple : [number , boolean , string];

myTuple = [000 , true , "Hello World"];
```

---

### Call Signatures

> 코드에 마우스 올리면 나오는 것

> Call signature는 함수의 타입을 정의하는 것이다.

```ts
type Add = (a: number, b: number) => number;

// or
// type Add = { (a: number, b: number) : number };

const doAdd: Add = (a, b) => a + b;
```

### Overloading

> 오버로딩은 함수가 여러개의 call signature를 가지고 있을때 사용한다.

```ts
type Add = {
  (a: number, b: number): number;
  (a: number, b: string): number;
};

const add: Add = (a, b) => {
  if (typeof b == "string") return a;
  return a + b;
};
```

```ts
type Config = {
  path: string;
  state?: number;
};

type Push = {
  (path: stirng): viod;
  (config: Config): void;
};

const push: Push = (config) => {
  if (typeof config === "string") {
    console.log(config);
  } else {
    console.log(config);
  }
};
```
