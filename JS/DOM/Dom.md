## DOM Document Object Model(문서객체모델)

- DOM은 문서를 논리 트리로 표현하고 각 **노드**는 객체를 갖는다.

* 자바스크립트가 DOM 구조에 접근하여 문서 구조, element의 스타일, 내용 등을 변경할 수 있다.

![domtree](https://www.freecodecamp.org/news/content/images/2021/09/Document.jpg)

```html
<html>
  <head>
    <title>TITLE</title>
  </head>
  <body>
    <h1>Title</h1>
    <h2>SubTitle</h2>
  </body>
</html>
```

---

`NODE`

- DOM은 Node의 계층 구조로 이루어져 있으며 각 노드는 부모와 children을 가질 수 있다.

* HTML에 있는 tag `<html>, <p>...`들은 node이다.  
   text 로 표현된 것들도 node가 된다.

`DOM Element`

- Element는 node의 특정 타입이며 HTML에서 태그로 적은 노드들을 지칭한다.
- `<html>, <div>, <title>` 과 같은 태그로 나타낸 것들은 전부 element이다.

##### 주석이나 text node와 같은 것들은 HTML 태그로 표현된 것이 아니므로 element가 아니다.
