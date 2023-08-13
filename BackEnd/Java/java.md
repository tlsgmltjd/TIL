## Java

- 객체 지향 언어로 개발된 프로그래밍 언어이다.
- 자바 가상 머신(JVM, Java Virtual Machine)을 사용하여 운영체제와 독립적으로 동작할 수 있다.
- 어느 운영체제에서나 같은 형태로 실행 가능하다.

```java
public class _01_HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

- `String`, `char`, `int`, `long`, `double`, `float`, `boolean` 등의 자료형이 있다.

```java

public class _03_Variables {
    public static void main(String[] args) {
        String name = "신희성";
        int hour = 17;
        System.out.println("내 이름은 " + name + " 나이는 " + hour);

        double score = 90.5;
        char grade = 'A';
        name = "강백호";
        System.out.println(name + " 님의 평균 점수는 " + score + " 점입니다.");
        System.out.println("학점은 " + grade + " 입니다");

        boolean pass = true;
        System.out.println("이번 시험에 합격했을까요? " + pass);

        // double과 flaot
        // double 좀 더 정밀
        double d = 3.14159265358979;
        float f = 3.14159265358979F;

        System.out.println(d);
        // -> 3.14159265358979
        System.out.println(f);
        // -> 3.1415927

        // int와 long
        // int i = 1000000000000;
        // -> Integer number too large

        // 정수 범위게 21억을 초과한다면 long형 자료형을 사용하자
        long l = 1000000000000L;
        l = 1_000_000_000_000L;
        System.out.println(l);

    }
}

```
