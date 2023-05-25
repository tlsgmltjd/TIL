## webStorage

- 웹 스토리지 (web storage)는 서버가 아닌, **클라이언트에 데이터를 저장**할 수 있는 기능이다.

---

### 로컬 스토리지 (Local Storage)

- 로컬 스토리지는 브라우저에 반영구적으로 데이터를 저장한다.
- **브라우저를 종료해도 데이터가 유지**되지만 다른 **도메인에선 접근이 불가능**하다.

### Local Storage

> **.setItem()** - key: value 추가  
> **.getItem()** - value 읽어 오기  
> **.removeItem()** - item 삭제  
> **.clear()** - 도메인 내의 localStorage 값 삭제  
> **.length** - 전체 item 갯수  
> **.key()** - index로 key값 찾기

```js
// 로컬 스토리지에 값 저장
localStorage.setItem(key, value);
```

```js
// key 값을 이용해서 로컬 스토리지에서 값 읽어오기
localStorage.getItem(key);
```

> 객체 / 배열을 저장 하려면 **JSON**객체의  
> .stringify / .parse 매소드를 이용하여 저장 / 읽어온다.

```js
// key 값을 이용하서 로컬 스토리지의 값 삭제하기
localStorage.removeItem(key);
```

```js
// 로컬 스토리지 모두 비우기
localStorage.clear();
```

---

### 세션 스토리지(Session Storage)

- 세션 스토리지는 각 세션마다 데이터가 개별적으로 저장
- 세션 스토리지는 로컬 스토리지와 다르게 **세션을 종료하면 데이터가 제거** 된다.

```js
// 세션 스토리지에 값 저장
sessionStorage.setItem(key, value);
```

```js
// key 값을 이용해서 값 불러오기
sessionStorage.getItem(key);
```
