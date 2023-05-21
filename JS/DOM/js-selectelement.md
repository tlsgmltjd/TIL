## 자바스크립트로 태그 선택하기

HTML id속성으로 태그 선택하기

```js
document.getElementById("id");
```

HTML class속성으로 태그 선택하기 class에 해당하는 태그 모음(HTMLCollection)

> 유사배열이다!

```js
document.getElementsByClassName("class");
```

HTML 태그 이름으로 태그 선택하기 tag에 해당하는 태그 모음(HTMLCollection)

> 유사배열이다!

```js
document.getElementsByTagName("tag");
```

css 선택자로 태그 선택하기 css 선택자에 해당하는 태그 중 가장 첫번째 태그 하나

```js
document.querySelector(".css");
```

css 선택자로 태그 선택하기 css 선택자에 해당하는 태그 모음(NodeList)

> 유사배열이다!

```js
document.querySelectorAll(".css");
```

---

### 유사 배열이란?

- 배열과 유사한 객체 ex) HTMLCollection, NodeList, DOMTokenList, ...

#### 특징

- 숫자 형태의 indexing이 가능하다.
- length 프로퍼티가 있다.
- 배열의 기본 메소드를 사용할 수 없다.
- Array.isArray(유사배열)의 리턴값은 false다.

---

### 이벤트와 이벤트 핸들링, 그리고 이벤트 핸들러

#### 이벤트

- 웹 페이지에서 발생하는 대부분의 일(사건)들  
  ex) 버튼 클릭, 스크롤, 키보드 입력, ...

#### 이벤트 핸들링

- 자바스크립트를 통해 이벤트를 다루는 일

#### 이벤트 핸들러

- 이벤트가 발생했을 때 일어나야하는 구체적인 동작들을 표현한 코드.  
  **이벤트 리스너**(Event Listener)라고도 부른다.

```js
const btn = document.querySelector("#myBtn");

btn.onclick = function () {
  console.log("Hello Codeit!");
};
```
