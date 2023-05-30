## constructor (생성자)

> 상속

- 객체를 편리하게 생성해주는 `기계` 같은 것 이다.
- **같은 객체**들을 **여러개** 생성하기 위해서 사용한다.

---

```js
function Students() {
  this.name = "Kim";
  this.age = 15;
}
```

- object 자료 복사 기계만들 땐 `function` 키워드를 사용한다.

* `this` 키워드는 새로 생성되는 오브젝트를 뜻 하고,
* 새로 생성되는 `오브젝트.name은` `'Kim'`을 할당해달라는 것이다.

---

```js
function Students() {
  this.name = "Kim";
  this.age = 15;
}

let Student1 = new Students();
let Student2 = new Students();
```

- 오브젝트를 뽑아낼 땐 `new` 키워드를 사용한다.

* 이렇게 사용하면 `비슷한 오브젝트`를 `독립적`으로 여러개 만들 때 코드 양이 줄어든다.

---

**이런 것을 상속 이라고 한다.**

- 상속해주는 것은 **부모**, 상속받는 오브젝트들은 **자식** 이라고 부른다.

---

> 예시 코드

```js
function Products(name, price) {
  this.name = name;
  this.price = price;
  this.Buga_Pee = function () {
    console.log((this.price * 1) / 10);
  };
}

let product1 = new Products("skrits", 50000);
let product2 = new Products("shoes", 60000);

product1.Buga_Pee();
```

---

### class 를 이용하여 constructor 만들기

```js
class father {
  constructor() {
    this.name = "Kim";
  }
}

let son = new father();
```

<br />

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

### Object.getPrototypeOf()

```js
class father {
  constructor() {
    this.name = "Kim";
  }
}

let son = new father();

console.log(son.__proto__);
console.log(Object.getPrototypeOf(son));
```

- `son.__proto__` == `Object.getPrototypeOf(son)`
