# 자바 리플랙션

구체적인 클래스 타입은 알지 못해도 그 클래스의 메서드, 필드에 접근할 수 있도록 해주는 자바 API이다.

intelliJ의 자동완성 기능, 스프링의 어노테이션이 리플랙션을 활용한 기술이다. (DI, Proxy 등등..)

### JVM

리플랙션은 거울에 비친 상 같이 클래스의 정보를 통해 똑같은 형태를 만들고 해당 클래스의 정보를 접근하거나 수정할 수 있게 해준다.

여기서 말하는 클래스의 정보는 **JVM의 메모리 영역에서 가져온다.**

어플리케이션을 실행하면 작성한 .java 코드가 .class 형태의 바이트 코드로 변환되고

이 정보들은 클래스 로더롤 통해 JVM 메모리 영역에 저장된다.

다시 정리하면, 어플리케이션이 실행되어 **JVM 메모리 영역에 런타임 시점에 접근하여 클래스 정보를 접근, 수정**할 수 있게 해주는 API이다.

### 사용

#### 클래스 정보 조회

JVM에 있는 클래스 정보를 조회하려면 아래와 같은 방법이 있다.

```java
Myclass myclass = new Myclass();

Class<?> c1 = myClass.getClass();
Class<?> c2 = Myclass.class();
Class<?> c3 = Class.forName("xxx.xxx.Myclass")

c1.getName(); // 이렇게 불러온 클래스의 정보를 조회할 수있다.
```

#### 리플렉션 메서드

| 메서드 이름       | 범위   |
| ----------------- | ------ |
| getXXX();         | public |
| getDeclaredXXX(); | 모두   |

- getXXX() : 상위 클래스와 상위 인터페이서를 상속한 메서드를 포함하여 public인 값들을 불러온다.
- getDeclaredXXX() : 접근 제어자의 관계 없이 헤당 클래스의 값들을 가져온다.

Field, Method, Constructor 등을 조회할 수 있다.

set(), invoke() 메서드를 사용해서 필드의 값을 수정하거나, 메서드를 실행시킬 수 있다.

> 예시 클래스

```java
class Human10 {
    public String name;
    private Integer age;

    public void hi() {
        System.out.println(this.name);
    }

    public Human10(String name, Integer age) {
        this.name = name;
        this.age = age;
    }

    public Integer getAge() {
        return age;
    }
}
```

#### 메서드 가져와서 실행시키기

```java
 public static void main(String[] args) throws Exception {
    Human human = new Human("히히", 10000000);

    Class<Human> hc = Human.class;

    Field name = hc.getField("name"); // getField()로 클래스의 필드 정보를 조회해옴
    name.set(human, "신희성"); // 불러온 필드를 set() 메서드를 통해 값을 주입해줌

    Field age = hc.getDeclaredField("age"); // getDeclaredField() 메서드를 사용해서 private 접근 제어자가 붙은 필드응 조회해옴
    age.setAccessible(true); // private 필드이기 때문에 setAccessible(true) 메서드를 사용하여 access 할 수 있게 해줌
    age.set(human, 18); // set() 메서드롤 값을 주입해줌

    Method hi = hc.getMethod("hi"); // getMethod() 메서드를 사용해서 메서드를 조회해옴
    hi.invoke(human); // invoke() 메서드로 메서드를 실행시킴

    System.out.println(human.getAge());
}
```

> console

```
신희성
18
```

### 마치며

리플렉션을 사용하면 애플리케이션 동작을 유연하게 만들 수 있지만 런타임에서 작동하기 때문에 컴파일 시점에서 오류를 잡을 수 없다는 큰 단점이 존재한다.

이 외에도 보안관련 문제, 속도 문제 등등 문제가 많아 자바 리플렉션은 유의하여 사용해야한다.

그러므로 프레임워크나 라이브러리 개발자가 아닌 일반 개발자라면 되도록이면 사용을 지양하는 것이 좋다.
