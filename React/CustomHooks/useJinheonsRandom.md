## useJinheonsRandom

- NPM에 올릴게 진헌아 ㅎㅎ

> useJinheonsRandom

```tsx
const useJinheonsRandom = (jujak = 0.5) => {
  const [result, setResult] = useState<"win" | "lose">();

  const diceRoll = (yourChoice: 0 | 1) => {
    setResult(
      (Math.random() < jujak ? yourChoice : !yourChoice) === yourChoice
        ? "win"
        : "lose"
    );
  };

  return [result, diceRoll];
};
```

### 사용법

`cosnt [result, diceRoll] = useJinheonsRandom()`

- **useJinheonsRandom(0.5)** : 처음에 선언할 때 아규먼트로 `0.0` ~ `1.0`의 값을 보낼 수 있음,  
  1에 가까울 수록`win` 확률이 올라감.

- **result** : 랜덤 값을 뽑아냈을 때 `"win"` or `"lose"` 문자열을 줌
- **diceRoll(`yourChoice`)** : 랜덤 값을 뽑아내는 함수, 아규먼트로 `0` or `1` 을 보내야 함. _(앞면 혹은 뒷면의 선택....)_

> App

```ts
export default function App() {
  const [result, diceRoll] = useJinheonsRandom();

  const [choice, setChoice] = useState("앞면");

  return (
    <div>
      <select
        onChange={(e: React.FormEvent<HTMLSelectElement>) => {
          setChoice(e.currentTarget.value);
        }}
      >
        <option value={choice}>앞면</option>
        <option value={choice}>뒷면</option>
      </select>
      <button
        onClick={() => {
          if (typeof diceRoll !== "function") return;
          diceRoll(choice === "앞면" ? 0 : 1);
        }}
      >
        던지기
      </button>
      <h1>{result}</h1>
    </div>
  );
}
```
