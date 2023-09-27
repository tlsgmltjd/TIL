## 익명 클래스

- 익명 클래스는 이름이 없는 클래스를 말한다.
- 프로그램에서 일시적으로 한번만 사용되어 재사용성없을때 사용한다.

### 선언

- 이런식으로 인터페이스나 추상 클래스로 선언한다.

```java
public interface Anonymous {
    public void hi();
}
```

```java
public abstract class Action {
    public abstract void exec();
}
```

### 사용

```java
Anonymous anonymous = new Anonymous() {
    @Override
    public void hi() {
        System.out.println("asd");
    }
};
anonymous.hi();
```

- 이렇게 구현체(or 상속받는 클래스) 를 만들 필요가 없을 때 사용할 수 있다.
