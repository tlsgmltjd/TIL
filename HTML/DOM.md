## DOM(Document Object Model)

- HTML 문서의 계층 구조를 나타내는 객체 모델이다

###

- DOM은 HTML 문서의 객체 기반 표현 방식이며  
  DOM의 개체 구조는 **노드 트리**로 표현된다.

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <title>Hello</title>
  </head>
  <body>
    <h1 id="title">DOM(Document Object Model)</h1>
    <h2 id="sub-title">문서 객체 모델</h2>
  </body>
</html>
```

- window
  - document
    - html
      - head
        - meta
        - title
      - body
        - h1
          - > DOM(Document Object Model)
        - h2
          - > 문서 객체 모델

---

- 이 DOM 트리에서 각 객체는 노드라는 용어로 불림
- 각 노드간의 관계를 **부모노드, 자식노드**
- 같은 위치의 노드를 **형제노드** 라고 표현

### 노드 타입

#### 요소노드(Element Node)

- 테그를 표현하는 노드

#### 텍스트 노드 (Text Node)

- 문자열을 표현하는 노드

> 일반적으로 텍스트 노드는 요소 노드의 자식 노드가 되고, 따로 자식 요소를 가질 수 없기 때문에 '잎 노드' 라고도 부름

그 이외에 **코멘트 노드**, **문서 노드** 등등 여러 노드가 있다.

---

- 자바스크립트를 이용하여 DOM 노드에 접근할 수 있다.
