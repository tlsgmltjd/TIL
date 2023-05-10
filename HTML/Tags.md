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

### 테이블 (table)

- 테이블의 행은 `<tr>` (Table Row)태그로 감싼다.  
  각 데이터들은 `<td>` (Table Data) 태그로 넣는다.

```html
<table>
  <tr>
    <td></td>
    <td>Premium</td>
    <td>Standard</td>
    <td>Basic</td>
  </tr>
  <tr>
    <td></td>
    <td>₩15,900</td>
    <td>₩10,900</td>
    <td>₩8,900</td>
  </tr>
  <tr>
    <td>화질</td>
    <td>최대</td>
    <td>FHD</td>
    <td>HD</td>
  </tr>
  <tr>
    <td>다운로드</td>
    <td>무제한</td>
    <td>월 30회</td>
    <td>불가</td>
  </tr>
</table>
```

##### 머리글

표에서 머리글은 `<thead>` 태그로 감싼다. 행은 `<tr>` 태그로 감싼다.  
 각 행 안에 있는 것들은 제목이기 때문에`<td>`가 아니라 `<th>`라는 태그를 사용한다.  
 본문에 해당하는 행들은 `<tbody>`라는 태그로 감싼다.

```html
<thead>
  <tr>
    <th></th>
    <th>Premium</th>
    <th>Standard</th>
    <th>Basic</th>
  </tr>
  <tr>
    <th></th>
    <th>₩15,900</th>
    <th>₩10,900</th>
    <th>₩8,900</th>
  </tr>
</thead>
<tbody>
  <tr>
    ...
  </tr>
  ...
</tbody>
```

#### 바닥글

표에서 바닥글은`<tfoot>` 태그로 감싼다.

```html
<tfoot>
  <tr>
    <th></th>
    <th>₩15,900</th>
    <th>₩10,900</th>
    <th>₩8,900</th>
  </tr>
</tfoot>
```

---

### 폼 (form)
