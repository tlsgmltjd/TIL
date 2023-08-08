## Emotion 👩‍🎤

```
npm i @emotion/react
```

---

### css()

- css 스타일 선언 내용을 인자로 받는다.
- 객체나 문자형으로 넘겨줄 수 있다.

> 객체

```js
return (
  <div
    css={css({
      backgroundColor: "yellow",
    })}
  >
    emotion
  </div>
);
```

> 문자형

```js
return (
  <div
    css={css`
      background-color: yellow;
    `}
  >
    emotion
  </div>
);
```

> ex

```js
const resultStyle = {
  미정: css`
    color: #9e9e9e;
    cursor: default;
  `,
  합격: css`
    color: #2174d8;
    cursor: default;
  `,
  불합격: css`
    color: #ff000f;
    cursor: default;
  `,
};

// ...

<S.FinalResultText css={resultStyle[isFinalResult ? finalResult : "미정"]}>
  {isFinalResult ? finalResult : "미정"}
</S.FinalResultText>;
```
