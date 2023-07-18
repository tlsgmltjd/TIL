## react-beautiful-dnd

- Drag and Drop 구현

```js
npm i react-beautiful-dnd
```

```js
npm i --save @types/react-beautiful-dnd
```

## 구조

### DragDropContext

- DragDropContext은 Drag and Drop이 일어나는 전체영역이다.

### Droppable

- Droppable은 Drop이 가능한 영역이다.
- Droppable는 `droppableId` 필수로 입력해야하며 Drop 될 고유한 ID이다.

- `provided.innerRef`를 참조하여 동작을 실행하는 매개변수인 **provided** 가 필수이다.
- `snapshot`은 동작시 dom 이벤트에 대하여 적용될 style 참조이다.

### Draggable

- Dragpable은 Drag가 일어나는 요소들으로 Droppable 영역안에서 움직일 요소들이다.
