## for...in / for...of 그리고 enumerable / iterable 속성

**for ... in : Object 함수**  
**for ... of : Array 함수**

## for ... in

`Object`

```js
let myObj = { name: "Kim", age: 30 };

for (let key in myObj) {
  console.log(myObj[key]);
}
```

> 반복할 때 마다 `key` 값은 `name, age` 이렇게 데이터의 `key` 값이 된다.

### for ... in 반복문 특징

### enumerable 한 값만 출력한다.

> Object 자료형을 만들 때 오브젝트에 키벨류만 저장되는 것이 아닌  
> 그 외에 숨겨진 속성 3개가 같이 저장된다!

```js
let myObj = { name: "Kim", age: 30 };

console.log(Object.getOwnPropertyDescriptor(myObj, "name"));
```

```js
{value: "Kim", writable: true, enumerable: true, configurable: true}
```

여기서 `enumerable` 이라는 속성이 `true`인 값만 `for ... in` 반복문을 사용할 수 있다.

> - enumerable -> `셀수있는`

### 부모의 prototype에 저장된 것도 출력한다.

```js
class father {}
father.prototype.name = "Park";

let myObj = new father();

for (let key in myObj) {
  console.log(myObj[key]);
}

// Park
```

이렇게 `Class`로 상속된 오브젝트는 부모의 `Prototype`에 있는 요소도 `for ... in` 반복문에서 출력된다.

#### 막기

```js
class father {}
father.prototype.name = "Park";

let myObj = new father();

for (let key in myObj) {
  if (myObj.hasOwnProperty(key)) {
    console.log(myObj[key]);
  }
}
```

> `Object.hasOwnProperty()` 라는 메서드와 조건문을 사용하여 부모의 `Prototype`을 출력하는 것을 막을 수 있다.

> `Object.hasOwnProperty()` - 오브젝트가 `key` 값을 직접 가지고 있는지 확인하는 메서드이다.

---

## for ... of

`Array`

```js
let myArray = [2, 3, 4, 5];
for (let data of myArray) {
  console.log(data);
}
```

> `for ... of` 반복문은 `Array` 뿐만 아니라

> `array, 문자, arguments, NodeList, Map, Set` 이라는 자료형에서도 사용이 가능하다.

**= 즉, iterable한 자료형들만 적용 가능하다.**

iterable한 자료형은

```js
[Symbol.iterator]();
```

이라는 일종의 메서드를 가지고 있는 자료형들을 말한다.

```js
let myArray = [2, 3, 4, 5];
console.log(myArray[Symbol.iterator]());

// Array Iterator { ... }
```
