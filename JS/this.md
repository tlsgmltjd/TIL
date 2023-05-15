## this

- this 키워드는 개체를 나타낸다.

### 1. 그냥 쓰거나 함수 안에서 쓰면 this는 window를 뜻한다.

```js
console.log(this);
```

```js
function coolFunction() {
  console.log(this);
}
coolFunction();
```

- window는 **모든 전역변수, 함수, DOM을 보관하고 관리하는 전역객체**이다.

#### 1-2. strict mode일 때 함수 안에서 쓰면 this는 undefined 이다.

```js
<script>
  'use strict'; function coolFunction() {console.log(this)}
  coolFunction();
</script>
```

- **use strict**라는 키워드를 페이지 최상단에 추가하면 **엄격 모드**로 실행됨
- **strict mode**에선 this 키워드를 **일반함수** 안에서 불렀을 때 **undefined라는 값으로 강제로 지정**된다.

---

### 2. 메서드에서 this를 쓰면 해당 객체를 참조한다

```js
let OBJ = {
  data: "Kim",
  coolFunction: function () {
    console.log(this);
  },
};
```

- **메소드안에서** this를 쓰면 this는 **메소드를 가지고 있는 오브젝트**를 나타냄
  > { data : 'Kim', coolFunction : f }

---

### 3. constructor 안에서 쓰면 constructor로 새로생성되는 오브젝트를 뜻 한다

```js
function Made() {
  this.이름 = "Kim";
}
```

- this는 **'Made'로부터 새로 생성될 오브젝트**를 뜻한다.

```js
function Made() {
  this.이름 = "Kim";
}
const OBJ = new Made();
```

> OBJ = { 이름 : "kim" }

---

### 4. eventlistener 안에서 쓰면 this는 e.currentTarget

```js
const btn = document.getElementById("버튼");
btn.addEventListener("click", function (e) {
  console.log(this);
});
```

- **e.currentTarget은 지금 이벤트가 동작하는 곳**

---

### 일반 콜백함수에서 this

```js
let OBJ = {
  이름들: ["진헌", "현", "재균"],
  함수: function () {
    OBJ.이름들.forEach(function () {
      console.log(this);
    });
  },
};
```

> this -> window

### Arrow Function에서 this

```js
let OBJ = {
  이름들: ["진헌", "현", "재균"],
  함수: function () {
    OBJ.이름들.forEach(() => {
      console.log(this);
    });
  },
};
```

> this -> 현재 객체
