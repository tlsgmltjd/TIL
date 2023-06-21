## useMemo

- **useMemo**는 리액트에서 컴포넌트의 성능을 최적화 하는데 사용되는 훅이다.

- useMemo에서 memo는 **memoization** 이라는 뜻이다.

> 컴퓨터 프로그램이 동일한 계산을 반복해야 할 때, 이전에 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거하여 프로그램 실행 속도를 빠르게 하는 기술이다.

**동일한 값을 반환하는 함수를 반복적으로 호출**해야한다면 **처음 값을 계산할 때 해당 값을 메모리에 저장**해 필요할 때마다 다시 계산하지 않고 메모리에서 꺼내서 재사용 하는 것이다.

 <br />

```js
function App() {
  const number = calculate();
  return <div>{number}</div>;
}

function calculate() {
  return 100;
}
```

- 컴포넌트가 랜더링 될 때마다 `number` 값이 초가화 되기 위해 매번 `calculate` 함수가 불필요하게 재호출된다.

- `useMemo` 훅을 사용한다면, `calculate` 함수를 반복적으로 실행할 필요가 없어진다.
- **처음에 계산된 값을 메모리에 저장해** **컴포넌트가 계속 렌더링되어도** `calculate`를 다시 호출하지 않고 **메모리에 저장되어있는 계산된 값을 가져와 재사용**할 수 있게 해준다

---

### useMemo

```js
const number = useMemo(() => {
  return calculate();
}, [item]);
```

> useMemo(callback function, [dependancyArray])

- 의존성 배열 안에있는 값이 업데이트 될 때에만 콜백 함수를 다시 호출하여 메모리에 저장된 값을 업데이트 한다. _like useEffect_

---

```js
const hardCalculate = (number) => {
  console.log("어려운 계산!");
  for (let i = 0; i < 99999999; i++) {} // 생각하는 시간
  return number + 10000;
};

const easyCalculate = (number) => {
  console.log("쉬운 계산!");
  return number + 1;
};

function App() {
  const [hardNumber, setHardNumber] = useState(1);
  const [easyNumber, setEasyNumber] = useState(1);

  const hardSum = hardCalculate(hardNumber);
  const easySum = easyCalculate(easyNumber);

  return (
    <div>
      <h3>어려운 계산기</h3>
      <input
        type="number"
        value={hardNumber}
        onChange={(e) => setHardNumber(parseInt(e.target.value))}
      />
      <span> + 10000 = {hardSum}</span>

      <h3>쉬운 계산기</h3>
      <input
        type="number"
        value={easyNumber}
        onChange={(e) => setEasyNumber(parseInt(e.target.value))}
      />
      <span> + 1 = {easySum}</span>
    </div>
  );
}
```

- 어려운 계산의 값을 변경 할 시 반복문을 99999999번 돌리기 때문에 약 1초정도의 딜레이가 발생한다.
- **하지만 쉬운 계산의 값을 변경해도 약 1초 의 딜레이가 걸린다.**

`state`가 변경되면 함수형 컴포넌트인 `App`이 리랜더링이 된다.  
그때, 내부 변수들이 초기화 되기 때문에 `hardCalculate`가 다시 실행된다.

<br />
<br />

```jsx
const hardSum = useMemo(() => {
  return hardCalculate(hardNumber);
}, [hardNumber]);
const easySum = easyCalculate(easyNumber);
```

이렇게 `hardCalculate` 함수를 실행하는 코드를 `useMemo` 사용하여 콜백함수로 넣고,  
 디펜던시 리스트에 `hardNumber` 값을 넣어 `hardNumber` 값이 수정될 때 마다 콜백함수를 실행하게 한다.

- 이렇게 하면 어려운 계산기의 값을 수정할 때만 `hardCalculate` 함수를 실행하게 한다.
