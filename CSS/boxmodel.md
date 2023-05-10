## 박스 모델

### padding (안쪽 여백)

```css
padding: 16px 8px 24px 10px;

=

padding-top: 16px;
padding-right: 8px;
padding-bottom: 24px;
padding-left: 10px;
```

### margin (바깥쪽 여백)

```css
margin: 16px 8px 24px 10px;

=

margin-top: 16px;
margin-right: 8px;
margin-bottom: 24px;
margin-left: 10px;
```

## ![박스모델](https://media.discordapp.net/attachments/1073625864392167494/1074232283973820436/margin-padding-summary-00.png?width=1434&height=807)

### border

```css
굵기, 테두리 종류, 색상
border: 2px solid #ededed;

border-radius (테두리 둥글게)
border-radius: 16px;
```

```css
border-radius: 50%; [타원]
border-radius: 9999px; [알약](아주 큰 값)
```

```css
box-sizing [border를 기준] #box {
  margin: 20px;
  padding: 30px;
  width: 100px;
}
#box 요소의 실제 너비는 100 + 30 + 30 = 160;
```

```css
추천 * {
  box-sizing: border-box;
}
```

#### overflow (박스 밖으로 내용이 삐져나왔을 때)

```css
넘치는 내용 감추기
overflow: hidden;

넘치면 스크롤 하게 만들기
overflow: auto;

항상 스크롤 하게 만들기
overflow: scroll;
```

### 마진 상쇄

세로 마진은 서로 겹쳐서 나타남  
(부모 자식 관계인 태그에선 padding 이나 border (경계)가 없을때)

```html
<div id="a">a</div>
<div id="b">b</div>
```

```CSS
#a {
margin: 30px;
}

#b {
margin: 20px;
}
```

`#a와 #b의 마진을 겹치면 둘 사이의 마진은 30px이 된다.`
