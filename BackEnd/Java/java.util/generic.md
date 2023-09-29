## Generic

- 데이터의 타입을 클래스 내부에서 지정하는 것이 아닌 외부에서 사용자에 의해 지정되어 사용되는 것을 의미한다.
- 제네릭을 사용하면 잘못된 타입이 들어올 수 있는 것을 컴파일 단계에서 방지 가능

### 제네릭 선언

- 제네릭 타입은 클래스 또는 인터페이스 이름 뒤에 <> 부호안에 타입 파라미터을 지정한다.
- 대부분 알파벳 한글자로 표현

```java
public class Class <T> { ... }
public interface InterFace <T> { ... }
```

---

### 제네릭 사용

- 클래스를 설계할 때 구체적인 타입을 명시하지 않고 타입 파라미터로 넣어두었다가 실제 설계된 클래스가 사용되어질 때 구체적인 타입을 지정하면서 사용할 수 있다.

```java
public class Box<E> {
    private E obj;

    public void setObj(E obj) {
        this.obj = obj;
    }

    public E getObj() {
        return obj;
    }
}
```

```java
public class BoxExam {
    public static void main(String[] args) {
        Box<Object> box = new Box<>();
        box.setObj(new Object());
        Object obj = box.getObj();

        Box<String> box2 = new Box<>();
        box2.setObj("hello");
        String str = box2.getObj();

        Box<Integer> box3 = new Box<>();
        box3.setObj(1);
        int number = box3.getObj();
    }
}
```

### 제네릭과 와일드 카드
