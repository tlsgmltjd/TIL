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
