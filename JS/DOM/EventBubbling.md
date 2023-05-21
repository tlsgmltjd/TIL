## 이벤트 버블링 (Event Bubbling)

- HTML 문서는 계층적으로 이루어져있다.  
  이러한 계층적 구조 특징 때문에 만일 HTML 요소에 이벤트가 발생할 경우 **연쇄적 이벤트 흐름**이 일어나게 된다.

  ![버블링](https://joshua1988.github.io/images/posts/web/javascript/event/event-bubble.png)

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

---

## 이벤트 캡처링(Event Capturing)

- 캡처링은 버블링과는 반대로 최상위 태그에서 해당 태그를 찾아 내려간다.

![캡쳐링](https://joshua1988.github.io/images/posts/web/javascript/event/event-capture.png)

---

## 이벤트 전파 막기

- 원하는 타깃에서만 이벤트를 발생하게 하고 싶을때 사용한다.  
  `event.stopPropagation()`
