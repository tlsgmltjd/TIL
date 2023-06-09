## Virtual DOM (가상돔)

우선 **돔** 이란

- `DOM(Document Object Model)` 문서 객체 모델이다.
- 돔은 `html element` 들을 트리 형태로 표현한 것이다.

**가상 돔** 이란

- **가상 돔**은 **실제 돔의 내용을 추상화시켜 똑같이 가지고 있는** **자바스크립트 객체**이며 메모리에 저장된다.
- 가상 돔은 실제 돔의 좀 더 가벼운 복사본이다.

#### react 에서는 가상 돔을 이용하여 돔을 조작하는 일을 빠르게 만들어준다.

---

### 돔을 이용하여 돔 요소를 조작하는 단계

`document.querySelector("#Title").style.color = "red";`

> 이런식으로 돔 요소를 변경 한다면

-> `브라우저가 변경하는 요소를 찾는다.`  
-> `해당 요소와 자녀 요소를 돔에서 제거한다.`  
-> `새롭게 수정된 요소로 교체한다.`  
-> `CSS를 다시 연산한다.`  
-> `레이아웃 정보 수정`  
-> `렌더링`

- DOM 트리를 업데이트 시키는 작업은 별로 무겁지 않지만

* 하지만 매번 **업데이트를 할 때마다 브라우저가 랜더링 하는 작업**은 꽤 복잡하고 시간이 걸린다!

---

### 가상 돔을 이용하여 돔 요소를 조작하는 단계

- 리액트는 항상 **두개의 가상 돔 객체**를 가지고 있다.

1. **렌더링 이전** 화면 구조를 담은 가상돔
2. **렌더링 이후** 보이게 될 화면 구조를 나타내는 가상돔

- 리액트는 새로 렌더링 해야할 상황이 생길 때 마다`(state 변경)` **가상 돔을 생성한다.**

* 그리고 업데이트 **이전의 내용을 담고있는 가상 돔**과 렌더링 **이후에 변경될 내용을 담고 있는 가상 돔**을 **비교**하여 정확히 **어느 요소가 변했는지 찾아낸다.**
  > 이러한 과정을 `diffing` 이라고 부른다.  
  > `diffing` 은 효울적인 알고리즘을 이용하여 바뀐 요소들을 굉장히 빨리 찾을 수 있다.
* 그리고 **바뀐 요소들만 화면에 렌더링** 해준다. `Reconciliation (재조정)`

- 이 `Reconciliation` 효율적인 이유는 **"Batch Update"** 때문이다.
- **"Batch Update"** 는 바뀐 **모든 요소들을** 집단으로 렌더링 해준다.
  > List 안에 10개의 요소가 변경되었다면, 10번 렌더링 하는 것이 아니라 한꺼번에 바뀐 모든 부분을 집단으로 렌더링 해준다.

---

### 정리

### 1.

- 리엑트의 가상 돔은 실제 DOM과 같은 내용을 담고 있는 복사본이다.  
  그리고 이 복사본은 자바스크립트 객체 형태로 메모리에 저장 되어있다.

### 2.

- 리엑트는 항상 두 개의 가상 돔을 가지고 있다.  
  첫 번째는 가상 돔의 변경 전의 내용을 담고 있고,  
  두번 째 가상 돔은 변경 이후에 보여질 내용을 담고 있다.

### 3.

- 변경된 내용이 화면에 새롭게 그려지기 이전, 곧 실제 돔이 변경되기 이전에  
  리엑트는 두개의 가상 돔을 비교하여 정확히 어떤 부분이 바뀌었는지 효율적으로 비교하여 파악한다.  
  그리고 이러한 내용을 `Diffing` 이라고 부른다.

### 4.

- `Diffing` 을 통해서 변경된 부분을 파악한 이후에, `Batch Update` 를 수행함으로 실제 돔에 한번에 적용시켜준다.  
  그리고 이러한 과정을 `Reconsiliation (재조정)` 이라고 한다.
