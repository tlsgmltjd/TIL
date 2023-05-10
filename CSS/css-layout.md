## CSS 레이아웃

---

## position

- 글의 흐름에서 벗어나서 요소를 자유롭게 배치할 때 쓰는 속성
- 위치를 정하는 기준에 대해서 top, right, bottom, left 속성으로 위치를 정할 수 있다.

### relative 포지션

```
요소의 원래 위치를 기준으로 배치한다. 이때 요소의 원래 자리는 그대로 차지하고 있다.
```

```css
.jinheon {
  position: relative;
  top: 15px;
  left: 10px;
}
```

### absolute 포지션

```
가장 가까운 포지셔닝이 된 조상 요소를 기준으로 배치된다.
이때 글의 흐름에서 완전히 빠져서, 요소의 원래 자리는 차지하지 않는다.
```

```css
.red {
  position: relative;
  top: 0;
  left: 10px;
}

.blue {
  position: absolute;
  right: 10px;
  bottom: 15px;
}
```

### fixed 포지션

```
브라우저 화면을 기준으로 고정된 배치이다.
글의 흐름에서 완전히 빠져서, 요소의 원래 자리는 차지하지 않는다.
```

```css
.red {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
```

### sticky 포지션

```
static처럼 원래 위치에 배치되어 있다가, 정해진 위치에 브라우저가 스크롤되면 그때부터 fixed처럼 고정되어 배치된다.
기본적으로는 static처럼 배치되기 때문에 요소의 원래 자리를 차지한다.
```

### z-index

```
값이 높을수록 화면에서 앞쪽
```

---

## Flexbox

```css
display: flex;
```

### 배치 방향

```
flex-direction을 사용하면 기본 축의 방향을 정할 수 있다.
이때 기본 값은 row이다. (row / column)
```

### 기본 축 정렬: justify-content

```
justify-content를 사용하면 기본 축 방향으로 정렬할 수 있다.
기본 값은 flex-start이다.
```

### 교차 축 정렬: align-items

```
교차 축 방향으로 정렬할 때는 align-items를 사용한다.
기본 값은 stretch(늘려서 배치하기)이다.
```

### 요소가 넘칠 때: flex-wrap

```
교차 축 방향으로 넘어가서 배치됨.
```

### 간격: gap

### 요소 늘려서 채우기: flex-grow

```
기본 값은 0, flex-grow 값이 클수록 많이 늘어난다.
```

### 요소 줄여서 채우기: flex-shrink

```
flex-shrink의 기본 값이 1이기 때문에 기본적으로 요소를 줄여서 배치하고, 0으로 지정하면 크기가 줄어들지 않는다.
flex-shrink 값이 클수록 상대적으로 많이 줄어든다.
```

---

## Grid

### 그리드 나누기

```css
display: grid;
```

```
grid-template-columns 속성으로 컬럼을, grid-template-rows 속성으로 로우를 나눌 수 있다.
```

```css
grid-template-columns: 100px 200px 100px;
grid-template-rows: 150px 200px;
```

### 유연한 크기 단위

```
fr 이라는 단위를 사용하면 플렉스박스처럼 전체 크기에 대해 상대적인 값을 지정할 수 있다.
```

```css
display: grid;
grid-template-columns: 1fr 1fr 1fr;
grid-template-rows: 150px 200px;
```

### 반복되는 값을 한 번에 쓰기

```css
display: grid;
grid-template-columns: repeat(3, 1fr);
grid-template-rows: 150px 200px;
```

### 최소, 최대값

```
화면 너비가 작아지더라도 컬럼의 너비는 200px보다 작아지지는 않고, 화면 너비가 넓어지면 컬럼의 너비는 1 : 1 : 1 비율로 늘어난다.
```

```css
display: grid;
grid-template-columns: repeat(3, minmax(200px, 1fr));
grid-template-rows: 150px 200px;
```

### 간격 넣기

```css
display: grid;
grid-template-columns: repeat(3, minmax(200px, 1fr));
grid-template-rows: 150px 200px;
gap: 20px 10px;
```

### 원하는 위치로 배치하기

![grid](https://media.discordapp.net/attachments/1087710509299679262/1089454678883967026/grid-summary-003.png?width=1434&height=807)

```css
grid-column: 2/4;
grid-row: 1/3;
```

```css
grid-column: 2 / span2;
grid-row: 1 / span2;
```

### 이름으로 배치하기

```css
ody {
  grid-template-areas:
    "s m"
    "p p";
}

.sidebar {
  grid-area: s;
}

.main {
  grid-area: m;
}

.player {
  grid-area: p;
}
```
