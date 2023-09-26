## interface

- 클래스를 작성할 때 기본이 되는 틀을 제공하면서, 다른 클래스 사이의 중간 매개 역할을 한다.

### 인터페이스 선언

- 인터페이스의 모든 필드와 메서드는 public static final(필드) 여야한다. (생략가능)

```java
public interface TV {
    public int MIN_VOLUME = 0;
    public int MAX_VOLUMN = 100;

    public void turnOn();
    public void turnOff();
    public void changeVolume(int volumn);
    public void changeChannel(int channel);
}
```

> 컴파일 시 아래와 같이 자동 변환

```java
public abstract void on();
public abstract void off();
public abstract void volume(int value);
public abstract void channel(int number);
```

### 인터페이스 구현

- 인터페이스는 사용할때 해당 인터페이스를 구현하는 클래스에서 implements 키워드를 사용한다.

- 인터페이스가 가지고 있는 메소드를 하나라도 구현하지 않는다면 해당 클래스는 추상클래스가 된다. (인스턴스를 만들 수 없다.)

- 참조변수의 타입으로 인터페이스를 사용할 수 있다. 이 경우 인터페이스가 가지고 있는 메소드만 사용할 수 있다.

```java
// TV라는 인터페이스를 구현하는 객체 -> LedTV
// TV 인터페이스가 가지고 있는 모든 기능들을 구현해야함
public class LedTV implements TV{
    @Override
    public void turnOn() {
        System.out.println("켜다");
    }

    @Override
    public void turnOff() {
        System.out.println("끄다");
    }

    @Override
    public void changeVolume(int volumn) {
        System.out.println(volumn);
    }

    @Override
    public void changeChannel(int channel) {
        System.out.println(channel);
    }
}
```
