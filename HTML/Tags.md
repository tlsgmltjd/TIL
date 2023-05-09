### 리스트 (list)

#### 순서 리스트(Ordered List)

```html
<h2>진헌이 순위</h2>
<ol>
  <li>모바일 로보틱스</li>
  <li>3D 모델링</li>
  <li>C++ 알고리즘</li>
  <li>3D 프린터</li>
  <li>사이버 보안</li>
  <li>프론트 엔드</li>
</ol>
```

#### 순서 없는 리스트(Unordered List)

```html
<h2>카테고리</h2>
<ul>
  <li>한국 영화</li>
  <li>외국 영화</li>
  <li>드라마</li>
  <li>예능</li>
  <li>영화</li>
  <li>프로야구</li>
</ul>
```

#### 리스트 스타일링

```html
<ol type="I">
  <li>라라랜드</li>
  <li>명량</li>
  <li>극한직업</li>
  <li>신과함께: 죄와 벌</li>
  <li>국제시장</li>
  <li>어벤져스: 엔드게임</li>
</ol>
```

```css
ul {
  list-style: disc; /* 동그라미 */
}

ul {
  list-style: none;
}

ul > li {
  display: inline-block;
}
```

---
