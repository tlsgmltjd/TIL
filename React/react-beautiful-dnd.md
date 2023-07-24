## react-beautiful-dnd

- Drag and Drop 을 쉽게 구현할 수 있는 라이브러리이다! 💅

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

```tsx
<Droppable droppableId={boardId}>
  {(provider, snapshot) => (
    <div
      isDraggingOver={snapshot.isDraggingOver}
      isDraggingFromThis={Boolean(snapshot.draggingFromThisWith)}
      ref={provider.innerRef}
      {...provider.droppableProps}
    >
      {toDos.map((toDo, index) => (
        <DragabbleCard
          key={toDo.id}
          toDoId={toDo.id}
          toDoText={toDo.text}
          index={index}
        />
      ))}
      {provider.placeholder}
    </div>
  )}
</Droppable>
```

### Draggable

- Dragpable은 Drag가 일어나는 요소들으로 Droppable 영역안에서 움직일 요소들이다.

- 움직일요소들이 가지는 고유값인 `draggableId` 를 필수로 입력해야한다.

- 마찬가지로 `provided.innerRef`를 참조하여 동작을 실행하는 매개변수인 **provided** 가 필수이다.
- `snapshot`은 동작시 dom 이벤트에 대하여 적용될 style 참조이다.

```tsx
<Draggable draggableId={toDoId.toString()} index={index}>
  {(provided, snapshot) => (
    <Card
      isDragging={snapshot.isDragging}
      ref={provided.innerRef}
      {...provided.dragHandleProps}
      {...provided.draggableProps}
    >
      {toDoText}
    </Card>
  )}
</Draggable>
```
