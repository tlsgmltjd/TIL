# getter, setter, constructor, builder

## getter, setter

- 객체 지향 프로그래밍에서 사용되는 개념이며, 일종의 메서드이다.
- Getter, Setter를 사용하여 객체 내부 속성에 직접 접근하지 않게 하여 객체의 정보를 은닉할 수 있다.
  - 이렇게 객체의 정보를 은닉하면 객체 지향 프로그래밍 4원칙 중 하나인 `캡슐화`를 구현할 수 있다.
  - `캡슐화` 란, 객체의 정보는 내부에 숨기고 외부에는 안정적인 부분만 공개하여 객체의 직접적인 데이터 변경을 막는다.
- Getter 는 객체의 속성 값을 반환하는 메서드이며 Setter는 객체의 속성 값을 설정, 변경하는 메서드이다.

### geter

- 객체의 속성 값을 반환하는 메서드이다.
- 보통 `get속성이름` 이 메서드 이름이 된다.

```java
class User {
    private String name = "hello";
    private int age = 17;

    public String getName() { // Getter
        return this.name;
    }
}
```

### setter

- 객체의 속성 값을 설정, 변경하는 메서드이다.
- getter와 마찬가지로 `set속성이름` 이 메서드 이름이 된다.
- 가급적 Setter 는 사용하지 않는 것이 좋다.
  - 값을 변경한 의도를 파악하기 힘들며 객체의 일관성 유지가 어렵기 때문이다.

```java
class User {
    private String name = "hello";
    private int age = 17;

    public void setName(String name) { // Setter
        this.name = name;
    }
}
```

### setter 대채품

### builder 패턴

```java
class User {
    private String name = "hello";
    private int age = 17;

    @Builder
    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

- 필요한 데이터만 이용하여 유현한 클래스 생성이 가능하다. 덕분에 객체 생성을 위한 생성자 오버로딩이 사라지고 전체 생성자 하나만 가지고 있는 형태가 되어 가독성이 향상된다.
- 또한 객체 생성시 인자 값의 순서가 상관 없다.

### 정적 팩토리 메서드

```java
class User {
    private String name = "hello";
    private int age = 17;

    public static void updateUserName(String name) {
        this.name = name;
    }
}
```

- 정적 팩토리 메서드를 사용 한다면 이름을 가질 수 있기 때문에 데이터 변경이 예측 가능하다.

## constructor

- 객체가 생성될때 자동으로 호출되는 특수 메서드로 객체의 초기화를 위해 사용된다.
- 생성자 이름을 클래스 이름과 동일 해야하고 반환 타입이 없다.
- 모든 클래스에는 반드시 하나 이상의 생성자가 정의되어야 함. (없을경우 컴파일러가 기본 생성자를 만들어줌)

```java
class User {
    private String name = "hello";
    private int age = 17;

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

- Lombok의 어노테이션을 사용하여 클래스의 생성자를 넣어줄 수도 있다.
- `@NoArgsConstructor`
  - 기본 생성자를 만들어준다.
- `@AllArgsConstructor`
  - 모든 필드를 초기화하는 생성자를 만들어준다.
- `@RequiredArgsConstructor`
  - 필수 필드(final 필드)를 초기화하는 생성자를 만들어준다.

## builder

- 객체를 생성하기 위한 패턴중 하나이다.
- 필요한 데이터만 유연하게 설정할 수 있어 가독성을 높일 수 있다.
- 생성자나 정적 팩토리 함수가 처리해야할 매개변수가 너무 많을때 빌더 패턴을 채택할 수 있다.
- Lombok 라이브러리의 `@Builder` 어노테이션으로 생성 가능.

```java
@Getter @Builder
class User {
    private String name;
    private int age;
    private int height;
    private int grade ;
    private String gender;
}
```

```java
User u = User.builder()
        .name("asd")
        .height(178)
        .age(123)
        .grade(1)
        .gender("Male")
        .build();
```

- 위와 같이 빌더 패턴을 사용하여 객체를 생성하면 필요한 값만 설정 가능하고 어떤 값을 설정하는지 명확히 알 수 있으며 설정 순서도 정해져 있지 않기 때문에 가독성이 향상된다.
