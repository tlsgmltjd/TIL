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

### align-content

```
line을 변경한다. line은 cross-axis
```

- justify-content와 비슷하지만 'line'에 관한 것

  > 각 block이 여러 행에 걸쳐 나올 때, 행간 공백을 얼마나 둘 것인지.

- align-content: flex-start; - align-content: `space-around`;

### align-self

```
부모가 아닌 자식 아이템의 위치(position)를 직접 변경하고 싶을 때 사용한다.
align-self는 align-item과 같이 동작한다.
```

### order

```
order의 경우 단어 그대로 순서를 바꾼다.
이때 기본 값(default)는 0이라 order를 1로 줄 경우 order를 주지 않은 것보다 뒤에 위치하게 된다!!
```

### 요소가 넘칠 때: flex-wrap

```
교차 축 방향으로 넘어가서 배치됨.
flexbox는 width보다도, '같은 줄'에 있도록 하는 것을 우선시 한다.
```

```js
flex-wrap: wrap;
// child의 사이즈를 모두 유지하면서 배치
// 가로로 꽉 찼다면 아래로 배치됨
flex-wrap: nowrap;
// child를 모두 같은 줄에 정렬함, 이때 width가 줄어들 수 있음
```

### reverse

```js
flex-direction: row-reverse; // or column-reverse;
// 오른쪽 or 왼쪽 에서부터 1이 시작

flex-wrap: wrap-reverse;
// 한 줄이 되지 않아도 아래에서 위로 정렬되게
```

### 간격: gap

### 요소 늘려서 채우기: flex-grow

```
기본 값은 0, flex-grow 값이 클수록 많이 늘어난다.

남아있는 공간, 여백이 있을 때만 grow 가능

화면이 커질 때, element도 함께 커지길 원할 때 사용

flex-grow property가 0인 상태거나, 따로 정의되지 않았다면,
화면이 커져도 각 element 크기가 커지지 않고 여백만 늘어난다.
```

### 요소 줄여서 채우기: flex-shrink

```
flexbox가 쥐어짤 때, element의 행동의 정의함

flex-shrink의 기본 값이 1이기 때문에 기본적으로 요소를 줄여서 배치하고, 0으로 지정하면 크기가 줄어들지 않는다.
flex-shrink 값이 클수록 상대적으로 많이 줄어든다.
```

```css
.a {
  flex-shrink: 1;
}
.b {
  flex-shrink: 2;
}
.c {
  flex-shrink: 1;
}
```

```
화면이 작아지면 숫자의 비율만큼 상대적으로 더 작아짐
```

### flex-basis

```
shrink, grow 되기전에 element에게 초기 size를 주는 것.

but 자주 사용 X basis 정의 안할시 width와 같은 값이니까.
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

### jutify-items / align-items

```css
justify-items: center;
align-items: center;

// short cut
place-items: center center;
```

```
grid cell 내부의 contents 의 배치방식을 일괄적으로 적용하는데 사용

▷ stretch : grid를 늘려서 grid를 채우게 한다. [기본값]
▷ start : item을 cell 시작에 배치한다.
▷ center : item을 cell 중앙에 배치한다.
▷ end : item을 cell 끝에 배치한다.
```

### justify-self / align-self

```css
align-self: center;
justify-self: Center
place-self: (수직) (수평);

▷ child에만 적용돠는 property이다.
```

### grid-auto

```css
● grid-auto-rows: 50px;
▷ 만들어놓은 row보다 더 많은 content가 있으면, 자동으로 (50px)row를 만들어라.

● grid-auto-flow: (방향); [기본값: row]
▷ flex-direction과 비슷하다.
▷ row가 끝날 때 새로운 row를 만들지, 새로운 column을 만들지 결정한다.

● grid-auto-columns: (크기);
▷ grid-auto-flow: column;일때 작동한다.
```

### justify-content / align-content

```
items는 각각의 cell을 의미한다면 content는 그리드 전체를 의미한다.
즉, 그리드 전체를 이동시킨다는 뜻
```

```css
justify-content: center;
align-content: center;

// short cut
place-content: center center;
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

### auto-fill / auto-fit

```
auto-fit, auto-fill은 전부 repeat() 함수 안에서만 동작한다.
repeat()의 첫번째 인자로 직접 숫자를 쓰는 것보다
auto-fill, auto-fit 둘 중 하나를 쓰는 것이 좋음
```

```css
grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
// 창 너비가 늘어나면 빈 column들로 row를 채움

grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
// 창 너비가 늘어나면 element를 늘려서 row에 맞게 해줌
```

### min-content max-content

```css
div 내부 컨텐츠에 따라서 셀의 크기를 조절하는 것.

grid-template-columns: max-content min-content;
// 1열은 컨텐츠를 나타내는 최대 사이즈로, 2열은 최소 사이즈로 열의 너비를 조정

Minmax와 결합가능

grid-template-columns: repeat(auto-fit, minmax(20px, max-content));

max-content를 최소값으로 두면, 컨텐츠를 다 싸고 있는 영역으로 최소값이 설정

min-content를 최소값으로 두면, 창이 줄었을 때, 컨텐츠가 들어갈 수 있는 최소한의 영역만 보존됨
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
