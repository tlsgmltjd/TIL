## class

- `class`를 사용하면 **객체 생성, 상속, 메서드 정의** 등을 더 간편하고 명확하게 할 수 있다.

### class 를 이용하여 constructor 만들기

```js
class father {
  constructor() {
    this.name = "Kim";
  }
}

let son = new father();
```

```js
class father {
  constructor() {
    this.sayHi = function () {
      console.log("hi");
    };
  }
  sayHello() {
    console.log("hello");
  }
}
```

- sayHi() 함수는 father 객체의 `메서드` 이고
- sayHello() 함수는 father 객체의 `prototype` 이다.  
  _(constructor() {} 외부에 있는)_

#### Object.getPrototypeOf()

```js
class father {
  constructor(name) {
    this.name = name;
  }
}

let son = new father("Kim");

console.log(son.__proto__);
console.log(Object.getPrototypeOf(son));
```

- `son.__proto__` == `Object.getPrototypeOf(son)`

---

## extends / super

- **class를 상속한 class**를 만들고 싶을 때 `extends` 키워드를 사용한다.

```js
class grandFather {
  constructor(name) {
    this.firstName = "Kim";
    this.lastName = name;
  }
}
```

> Class를 사용해 만든 constructor

```js
class father extends grandFather {}
```

> 이렇게 사용하면 `grandFather class`를 상속받는 `father class`를 만들 수 있지만...

```js
class father extends grandFather {
  constructor() {
    super();
  }
}
```

> super() 을 사용해야 부모 클래스의 constructor() 내용을 사용할 수 있다.

- **super()** 은 : **extends로 상속중인 부모 class의 constructor()** 를 의미한다.

---

> 예시코드

```js
class grandFather {
  constructor(name) {
    this.firstName = "Kim";
    this.lastName = name;
  }
}

class father extends grandFather {
  constructor(name) {
    super(name);
    this.age = 50;
  }
}

let daughter = new father("태연");
```
