## TypeScript?

- **타입스크립트는 자바스크립트에 타입을 부여한 언어**이다.  
  자바스크립트와 문법은 동일하고 타입 부분을 추가한 확장된 언어이다.

![ts](https://velog.velcdn.com/images/taeg92/post/a0e7e32b-49ee-4f17-ad61-a89f481521e3/Typescript.jpg)

### TypeScript의 장점

- 코드 작성 단계에서 부터 타입을 체크하고 오류를 확인하여 개발 중 실수를 미연에 방지할 수 있다.

* **정적 타입을 지원한다.**

```js
function multiplication(a, b) {
  return a * b;
}
```

> 자바스크립트  
> 어떤 타입의 인수를 전달하여야 하는지, 어떤 타입의 반환값을 리턴해야 하는지 명확하지 않다.

```ts
function multiplication(a: number, b: number): number {
  return a * b;
}
```

> 타입스크립트  
> 전달할 인수의 타입, 반환될 값의 타입을 정해주어 의도를 명확하게 밝히며 가독성을 높히고 디버깅을 쉽게 한다!
