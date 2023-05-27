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

**element.innerHTML**  
요소 노드 내부의 HTML 코드를 문자열로 리턴해 준다.  
`(내부에 있는 줄 바꿈이나 들여쓰기 모두 포함한다.)`

```javascript
const myTag = document.querySelector("#list-1");

// innerHTML
console.log(myTag.innerHTML);
```

```
<li>AAAAAAA</li>
<li>asdasd</li>
<li>asdasddas</li>
<li>asdasd</li>
```

**element.outerHTML**  
요소 노드 자체의 전체적인 HTML 코드를 문자열로 리턴해준다.  
`(내부에 있는 줄 바꿈이나 들여쓰기 모두 포함한다.)`

```js
const myTag = document.querySelector("#list-1");

// outerHTML
console.log(myTag.outerHTML);
```

```
<ul id = "list-1">
  li>AAAAAAA</li>
  <li>asdasd</li>
  <li>asdasddas</li>
  <li>asdasd</li>
</ul>
```

**element.innerText**  
요소 안의 내용들 중에서 HTML 태그 부분은 제외하고 텍스트만 가져온다.  
`(내부에 있는 줄 바꿈이나 들여쓰기 모두 포함한다.)`

```js
const myTag = document.querySelector("#list-1");

// textContext
console.log(myTag.textContent);
```

```
AAAAAAA
asdasd
asdasddas
asdasd
```

**요소 노드 만들기**: document.createElement('태그이름')  
**요소 노드 꾸미기**: element.textContent, element.innerHTML, ...  
**요소 노드 추가 혹은 이동하기**: element.prepend, element.append, element.after, element.before  
**요소 노드 삭제하기**: element.remove()

```js
// 요소 노드 추가하기
const tomorrow = document.querySelector("#tomorrow");

// 1. 요소 노드 만들기: document.createElement('태그이름')
const first = document.createElement("li");

// 2. 요소 노드 꾸미기: textContent, innerHTML, ...
first.textContent = "처음";

// 3. 요소 노드 추가하기: NODE.prepend, append, after, before
tomorrow.prepend(first);
```

### 스타일 다루기

**style 프로퍼티 활용하기**

```
element.style.styleName = 'value';
```

**class 변경을 통해 간접적으로 스타일 적용하기**

```
element.className, element.classList
```

### classList의 유용한 메소드

**classList.add**  
클래스 추가하기 여러 개의 값을 전달하면 여러 클래스 추가 가능  
**classList.remove**  
클래스 삭제하기 여러 개의 값을 전달하면 여러 클래스 삭제 가능  
**classList.toggle**  
클래스 없으면 추가, 있으면 삭제하기  
`하나의 값만 적용 가능하고, 두 번째 파라미터로 추가 또는 삭제 기능을 강제할 수 있음`

```js
const title = document.querySelector(".title");
```
