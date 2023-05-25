## setTimeout, setInterval

### setTimeout()

```
setTimeout(function, ms)
```

```js
setTimeout(() => console.log("실행!"), 5000);
```

- 일정 시간 후 파라미터로 받은 콜백함수를 실행해준다.

#### clearTimeout()

- setTimeout() 함수는 **타임아웃 아이디**(Timeout ID)라고 불리는 숫자를 반환한다.
- 타임아웃 아이디는 setTimeout() **함수를 호출할 때 마다 내부적으로 생성되는 타이머 객체를 가리키고 있다**.
- 이 값을 clearTimeout()의 인자로 함수를 호출하면 해당 타이머를 삭제할 수 있다.

```js
const timer = setTimeout(() => console.log("곧 실행될 예정"), 5000);
clearTimeout(timer);
```

---

### setInterval()

```
setInterval(function, ms)
```

```js
setInterval(() => console.log("Tik!", 1000));
```

- setInterval() 함수는 어떤 코드를 일정한 시간 간격을 두고 반복해서 실행한다.

#### clearInterval()

- setInterval()은 타임아웃 아이디와 비슷하게 **인터벌 아이디(Interval ID)** 라는 숫자를 반환한다.
- 그리고 이 값을 인자로 사용하여 clearInterval() 함수를 호출하면 **함수가 주기적으로 실행되는 것을 막을 수 있다.**

```js
const intervalId = setInterval(() => console.log("Tok!", 500));
clearInterval(intervalId);
```
