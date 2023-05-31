## getter setter

- getter, setter 은 데이터를 보호하기 위해 사용한다.

```js
let obj = {
  get getter() { return ... },

  set setter(value) {},
};
```

- getter / setter 를 사용하면 함수를 일반 프로퍼티처럼 사용 가능하다.
- `()` 없이 사용 가능

**getter**

```js
obj.getter;
```

**setter**

```js
obj.stter = 999;
```

---

`set` 함수는 데이터를 입력해서 수정해주는 함수이기 때문  
 -> **파라미터가 한개 꼭 존재해야함**

`get` 함수는 데이터를 가져오는 함수 이기 때문  
-> **파라미터가 꼭 존재해야하고 함수 내에 `return`이 있어야함**

---

> `class` 에서 `getter / setter` 사용한 예시

```js
class Man {
  constructor() {
    this.name = "Lee";
    this.age = 17;
  }

  get nextAge() {
    return this.age + 1;
  }
  // getter 함수 만듬

  set setAge(age) {
    this.age = age;
  }
  // setter 함수 만듬
}

let jinheon = new Man();

console.log(jinheon.nextAge); // getter 함수 사용
// 18

jinheon.setAge = 20; // setter 함수 사용
console.log(jinheon.age);
// 20
```
