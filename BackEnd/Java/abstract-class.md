## 추상 클래스

- 하나 이상의 추상 메서드를 포함하는 클래스를 추상 클래스라고 한다.
- 이러한 추상 클래스는 객체지향프로그래밍에서 중요한 역할인 다형셩을 가지는 메서드의 집합을 정의할 수 있게 해주는 레전드이다.
- 추상 클래스는 인스턴스를 생성할 수 없다.

**추상 메서드**

- 자식 클래스에서 반드시 오버라이딩해야만 사용할 수 있는 메소드이다.
- 추상 메서드가 포함된 클래스를 상속받는 자식 클래스가 반드시 추상 메서드를 구현해야한다.

```java
abstract void hello();
```

- 추상 메소드는 선언부만이 존재하며, 구현부는 없다.

---

```java
abstract class Bird {
    public abstract void sing();
    public void fly() {
        System.out.println("날다");
    }
}

class Duck extends Bird {
    @Override
    public void sing() {
        System.out.println("꽥꽥");
    }
}

public class Main {
    public static void main(String[] args) {
        Duck duck = new Duck();
        duck.sing();
        duck.fly();

        Bird b = new Bird();
        // 추상 클래스는 부모의 역할은 가능하지만
        // 추상 클래스만으로 객체를 생성하진 못한다.
    }
}
```
