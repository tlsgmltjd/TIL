## Template Tagged literals

### Template literals

```js
let value = `Hi
Welcome!
`;
```

```js
let value = `Hi ${name} !`;
```

> ' `' 백틱 으로 사용하면 **엔터키사용**, **문자열 중간에 변수**를 집어넣는데 용의하다.

---

### Tagged Literals

```js
let name = "손흥민";

function investigator(strings, value) {
  console.log(strings);
  console.log(value);
}

investigator`안녕하세요 ${name} 입니다`;
```

```js
// ['안녕하세요 ', ' 입니다', raw: Array(2)]
// 손흥민
```

> 첫번째 파라미터 문자들은 `백틱` 내의 순수 문자만 골라서 Array로 만들어놓은 파라미터이다.

> 둘째 파라미터 부터 변수들은 `백틱` 내의 ${} 변수를 담는 파라미터이다.
