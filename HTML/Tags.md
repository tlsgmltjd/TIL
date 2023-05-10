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

- 기본적인 폼의 형태

```html
<form>
  <label for="username">아이디</label>
  <input id="username" name="username" />

  <label for="password">비밀번호</label>
  <input id="password" name="password" type="password" />

  <button>로그인</button>
</form>
```

- type 속성을 사용하면 다양한 인풋을 사용할 수 있다.

```html
<label for="password">비밀번호</label>
<input id="password" name="password" type="password" />
```

- 값이 비어있을 때 보여주는 값 placeholder

```html
<input name="username" placeholder="이메일 또는 휴대전화" />
```

- 반드시 입력해야 하는 값 required

```html
<input name="email" type="email" required />
```

- 자동 완성 autocomplete

```html
<input name="search" type="text" autocomplete="on" />
```

---

#### 체크박스 checkbox

한 항목만 선택하는 경우

```html
<label>
  <input name="agreement" type="checkbox" />
  동의합니다
</label>
```

날짜 date
선택한 날짜로 값을 지정할 수 있다.

```html
<input name="birthdate" type="date" />
```

파일 file

```html
<input name="avatar" type="file" />
```

파일 형식 지정하기
accept라는 속성을 써서 허용할 파일 확장자들을 정해 줄 수 있다.

```html
<input name="avatar" type="file" accept=".png,.jpg" />
```

파일 개수 지정하기

```html
<input name="photos" type="file" mutliple />
<!-- 여러 개 선택 가능 -->
<input name="avatar" type="file" />
<!-- 한 개만 선택 가능 -->
```

이메일 email

```html
<input name="email" type="email" />
```

숫자 number

```html
<input type="number" />

<!-- 100에서 1000사이 -->
<input type="number" min="100" max="1000" />

<!-- 100에서 1000사이, 버튼을 눌렀을 때 100씩 증가, 감소 -->
<input type="number" min="100" max="1000" step="100" />
```

비밀번호 password

```html
<input type="password" />
```

라디오 radio
동그란 선택 버튼입니다. 체크박스와 다르게 여러 항목 중 하나의 항목만 선택할 수 있다.

```html
<input id="very-bad" name="feeling" value="0" type="radio" />
<label for="very-bad">아주 나쁨</label>
<input id="bad" name="feeling" value="1" type="radio" />
<label for="bad">나쁨</label>
<input id="soso" name="feeling" value="2" type="radio" />
<label for="soso">보통</label>
<input id="good" name="feeling" value="3" type="radio" />
<label for="good">좋음</label>
<input id="very-good" name="feeling" value="4" type="radio" />
<label for="very-good">아주 좋음</label>
```

범위 range

```html
<label for="signup-feeling">현재 기분</label>
<input id="signup-feeling" name="feeling" min="1" min="10" type="range" />
```

텍스트 text

```html
<input name="nickname" type="text" />
```

옵션 선택 `<select>`

```html
<label for="genre">장르</label>
<select id="genre" name="genre">
  <option value="korean">한국 영화</option>
  <option value="foreign">외국 영화</option>
  <option value="drama">드라마</option>
  <option value="documentary">다큐멘터리</option>
  <option value="vareity">예능</option>
</select>
```

긴 글 `<textarea>`

```html
<textarea name="content"></textarea>
```
