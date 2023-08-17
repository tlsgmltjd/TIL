## 객체지향프로그래밍

> Object-Oriented Programming

컴퓨터 프로그래밍의 패러다임 중 하나이다.  
객체지향프로그래밍은 컴퓨터 프로그래밍을 여러 개의 독립적인 단위(객체)들의 모임으로 보는 것이다.

```java
Book b = new Book();

// b <- 참조형 변수
// Book <- 레퍼런스 타입
// Book() <- 생성자

// Book 이라는 인스턴스가 힙에 생성됨
// 이걸 참조하는 변수를 참조형 변수라고 함
```

- 클래스

  > 설계도면

  - 필드(속성)와 메소드(클래스의 기능)를 가진다

```java
class Dog {
    String name;
    int age;

    void bark() {
        System.out.println("멍멍!");
    }
}
```

- 오브젝트 / 인스턴스

  - 클래스를 기반으로 생성된 실제 객체

  > 실제 만들어진 것

```java
Dog myDog = new Dog();
myDog.name = "Buddy";
myDog.age = 3;
myDog.bark(); // 출력: 멍멍!
```

- 참조형 변수

  - 참조형 변수는 객체의 위치를 저장하며, 생성된 인스턴스에 대한 접근을 제공한다.

```java
Dog yourDog = myDog; // yourDog는 myDog를 가리키는 참조
yourDog.name = "Max";
System.out.println(myDog.name); // 출력: Max
```
