## CSS(Cascading Style Sheets)

- 웹페이지에 시각적 표현을 입히는 언어이다.  
  실제 화면에 표시되는 콘텐츠를 꾸며주는 시각적인 표현을 담당한다.

#### CSS 선택자

```css
선택자 {
  속성: 속성값;
  속성: 속성값;
}
```

---

### 태그 이름

그 태그에 해당하는 요소들에 모두 스타일을 적용

```css
h3 {
  font-size: 24px;
}
```

### 아이디 (id) 중복 사용이 안됨

```css
#아이디-이름
```

```html
id = "아이디-이름"
```

```html
<h3>우도</h3>
<h3 id="hallasan">한라산 국립공원</h3>
```

### 클래스 (class)

```css
.클래스이름
```

```html
class = "클래스이름"
```

```html
<h3 class="place">우도</h3>
```

---

## 단위

### 색상 단위

```css
색상 코드 #FFFF00
RGB rgb(255, 255, 0)
RGBA rgba(255, 255, 0, 0.5)
```

### 절대적인 크기 단위

```
픽셀 px
```

### 상대적인 크기 단위

```
퍼센트 %
부모 태그의 크기에 상대적으로 지정
```

```html
<div id="parent">
  <div id="child"></div>
</div>
```

```CSS
#parent { height: 320px; }
#child { height: 50%; }
```

### em

```
부모 태그의 크기를 상대적으로 사용
```

```HTML

<div id="parent">
    16px
  <div id="child">
    64px
  </div>
</div>
```

```CSS
#parent {
font-size: 16px;
}

#child {
font-size: 4em;
}
```

### rem

```
최상위 태그를 상대적으로 사용
```

```HTML
<html>
  <body>
    18px
        <div id="other">
            32px
        </div>
  </body>
</html>
```

```CSS
html {
font-size: 16px;
}

body {
font-size: 18px;
}

#other {
font-size: 2rem;
}
```

---

### 자주 쓰는 CSS 속성

```css
TEXT

글자 색 color
글자 크기 font-size
글꼴 font-family
글자 굵기 font-weight
줄 높이 line-height
텍스트 꾸미기 text-decoration: none, underline, line-through 등
```

```css
BackGround

이미지 넣기 background-image: url('flowers.png');
배경의 위치 background-position: center;
배경의 반복 background-repeat: no-repeat;
배경의 크기 background-size: cover;
```

```css
gradient

background-image: linear-gradient(#000000, #ffffff);
각도 변경 단위 (deg)
background-image:
  linear-gradient(45deg, rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.2));
```

```css
shadow

가로, 세로, 흐린 정도, 퍼지는 정도, 색상
box-shadow: 5px 10px 15px 8px rgba(0, 0, 0, 0.6);

불투명도
opacity: 1;
```

---

## 선택자+

### 선택자

```
선택자 {
  선언;
  선언;
  선언;
}
```

### 선택자 목록

#### 콤마(,)로 선택자를 연결하면 여러 선택자에 같은 규칙을 적용할 수 있음

```css
선택자1,
선택자2 {
  ...;
}
```

### 선택자 붙여 쓰기

#### 여러 조건을 동시에 만족하는 요소를 선택

```html
<h2 id="mongolia" class="large title">진헌이</h2>
```

```CSS
예시 1. 아이디 + 클래스
#mongolia.title
예시 2. 클래스 + 클래스
.large.title
예시 3. 태그 + 아이디 + 클래스
h2#mongolia.large.title
```

---

### 자식 결합자 (Child Combinator)

오른쪽 꺾쇠로 선택자를 이어줌

```HTML
<div class="article">
  <img src="tesla-y-2025.png">
  ...
</div>
```

```CSS
.article > img {
width: 100%;
}
```

### 자손 결합자 (Descendant Combinator)

스페이스(띄어쓰기)로 선택자를 이어 줌

```HTML
<div class="article">
    <p> 이번에 리뷰해 볼 진헌이는 로보틱스 진헌이입니다.
      <img src="tesla-w-2025.png">
  </p>
  ...
</div>
```

```CSS
.article img {
width: 100%;
}
```

### 가상 클래스 (Pseudo-class)

```
:hover(마우스를 올렸을 때),
:active(클릭한 상태)
:visited(방문한 적이 있는 링크),
:focus(포커싱 됐을 때)
```

```css
a {
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
```

---

```
모든 요소를 선택하기
* {
  box-sizing: border-box;
}

.gallery의 모든 자식 요소 선택하기

.gallery > * {
  width: 120px;
  height: 90px;
}

n번째 자식 선택자(n-th child Selector)
ex. 숫자, even, odd, 2n

.gallery :nth-child(3) { ... }

.gallery :first-child { ... }
.gallery :last-child { ... }
```
