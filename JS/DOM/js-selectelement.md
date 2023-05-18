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

---

## 이벤트 버블링 (Event Bubbling)

- HTML 문서는 계층적으로 이루어져있다.  
  이러한 계층적 구조 특징 때문에 만일 HTML 요소에 이벤트가 발생할 경우 **연쇄적 이벤트 흐름**이 일어나게 된다.

```js
<form onclick="alert('form')">
  FORM
  <div onclick="alert('div')">
    DIV
    <p onclick="alert('p')">P</p>
  </div>
</form>
```

`p를 클릭`

-> `alert('p')` -> `alert('div')` -> `alert('form')`

> 이 순서로 실행

**버블링(Bubbling)** : 자식 요소에서 발생한 이벤트가 바깥 부모 요소로 전파된다!

**캡쳐링(Capturing)**: 자식 요소에서 발생한 이벤트가 부모 요소부터 시작하여 안쪽 자식 요소까지 도달한다!

---

### 이벤트 전파 흐름

1. **캡처링 단계** : 이벤트가 하위 요소로 전파되는 단계
2. **타깃 단계** : 이벤트가 실제 타깃 요소에 전달되는 단계
3. **버블링 단계** : 이벤트가 상위 요소로 전파되는 단계
