## 내부 클래스

- 클래스 내부에 생성된 클래스이다.

### 인스턴스 클래스

- 클래스의 필드를 선언하는 위치에 선언되는 경우이다. (중첩 클래스 or 인스턴스 클래스)

- `외부클래스.내부클래스` 형식으로 내부 클래스를 초기화 한다.

```java
public class Inner1 {
    class Cal {
        int value = 0;
        public void plus() {
            value++;
        }
    }

    public static void main(String[] args) {
        Inner1 i = new Inner1();
        Inner1.Cal cal = i.new Cal();
        cal.plus();

        System.out.println(cal.value);
    }

}
```

### 스태틱 클래스

- 내부 클래스가 static으로 정의된 경우이다. (정적 중첩 클래스)

- 이 경우에는 Inner2 객체를 생성할 필요 없이 Inner2.Cal() 로 객체 생성이 가능하다.

- 정적 메소드가 있다면 `클래스.정적내부클래스.정적메소드()` 이렇게 호출도 가능

```java
public class Inner2 {
    static class Cal {
        int value = 0;
        public void plus() {
            value++;
        }
    }

    public static void main(String[] args) {
        Inner2.Cal cal = new Inner2.Cal();
        cal.plus();
        System.out.println(cal.value);
    }
}
```

### 지역 클래스

- 메서드 안에 클래스를 선언한 경우이다. (지역 중첩 클래스, 지역 클래스)
- 지역변수처럼 메서드 안에서 해당 클래스를 사용가능.
  - 마찬가지로 static 키워드는 X
  - 메서드 내부에서만 사용되므로 접근제어자를 붙힐 필요가 없다.

```java
public class Inner3 {
    public void exec() {
        class Cal {
            int value = 0;
            public void plus() {
                value++;
            }
        }
        Cal cal = new Cal();
        cal.plus();
        System.out.println(cal.value);
    }

    public static void main(String[] args) {
        Inner3 inner3 = new Inner3();
        inner3.exec();
    }
}
```

### 익명 클래스

> 추가 문서로 서술
