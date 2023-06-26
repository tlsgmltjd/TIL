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

### polymorphism - Generic

> 함수가 사용할 타입을 미리 정해놓지 않고, 그 함수를 사용할 때 결정할 수 있도록 하는 것이다.

> 함수에서 다양한 타입이 필요한 경우, 모든 경우의 수에 해당하는 `Call signature`를 정의해놓는 것은 번거롭기 때문에,  
> 함수의 타입을 `generic`으로 설정해놓으면, 함수가 사용될때 타입을 알아서 유추 하도록 할 수 있다.

```ts
type Print = {
  <T>(arr: T[]): T;
  // 배열의 요소, return type를 알아서 유추해서 사용해줌
};

const print: Print = (arr) => arr[0]; // 배열의 첫번째 요소를 리턴

print([1, 2, 3]); // (arr: number[]) => number
print(["a", "b", "c"]); // (arr: string[]) => string
print([1, "a", 2, "b"]); // (arr: (string | number)[]) => string | number
```
