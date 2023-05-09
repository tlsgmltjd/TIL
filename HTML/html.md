## HTML(Hypertext Markup Language)

- 웹 페이지를 구성하는 기본적인 구성 요소이며, 웹 페이지의 구조와 내용을 정의하는 마크업 언어이다.

## HTML의 구성요소

### 테그(tag)

- 웹문서를 구성하는 명령어.

```html
<p>Hello</p>
```

### 요소(Element)

- HTML에서 요소는 시작태그와 종료태그, 그 사이의 내용

##### 블록 요소

위에서 아래로 차례대로 배치되는 요소.  
부모 요소의 너비 전체를 차지.

```
<div>, <p>, <h1>, <ul>, <li> ...
```

##### 인라인 요소

글을 쓰는 방향으로 줄이 바뀌면서 배치  
인라인 요소는 부모 요소의 너비를 차지하지 않음.

```
<span>, <a>, <img>, <strong>, <em> ...
```

##### 빈 요소

빈 요소는 종료 태그가 없는 요소

```
<img />, <br />, <hr /> ...
```

## 속성

- 속성은 요소에 대한 추가 정보를 제공한다.  
  속성은 시작 태그에 추가하며, 속성의 이름과 값을 지정한다.

#### 속성값

- 속성뒤에 ""안에 넣어줄 내용들

```html
<a href="속성값"> Hello </a>
```

---

## HTML 문서 기본 구조

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <title>Hello</title>
  </head>
  <body>
    <h1>Hello</h1>
  </body>
</html>
```

#### 독타입 (`<Doctype>`)

- HTML문서의 맨 처음에 명시하는 부분으로 문서의 버전에 관한 정보를 나타낸다.

#### HTML (`<html>`)

- 문서의 시작과 끝을 알리는 태그 시작 ＜ html ＞ 끝 ＜/html ＞ 해당 웹 문서가 HTML 언어로 작성된 문서임을 브라우저에게 알리는 역할

#### 헤드 (`<head>`)

- 웹 페이지에는 직접적으로 보이지 않는 정보  
  `ex) 페이지의 제목 <title>`

#### 바디 (`<body>`)

- 브라우저 화면에 보이는 것들

```html
<body></body>
```

#### 주석 (`comment <!-- -->`)

```html
<!-- 주석이다 -->
```