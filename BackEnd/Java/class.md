## Class

객체를 만들어 내기 위한

```
접근제한자 class 클래스이름 {

    필드들;

    생성자들;

    매서드들;
}
```

#### 접근 제한자

- 클래스의 외부에서 해당 클래스에 접근할 수 있는 범위를 지정

#### 필드들

- 클래스 내부에 속하는 변수들을 필드라고 부른다!

#### 생성자들

- 클래스의 인스턴스를 생성할 때 호출되는 특별한 메서드이다.  
   객체 초기화를 위해 사용되며, 인스턴스를 생성할 때 필드를 초기화하는 데 사용된다.

#### 메서드들

- 클래스 내부에 선언된 함수를 메서드라고 한다.

#### UML 표기법

> getOne() :int  
> printNumber(int) :void

```java
package chap_01;

class VendingMachine {

    // field
    // 생성자
    // method

    public String pushProductButton(int menuId) {
        System.out.println(menuId + " 를 전달 받았습니다.");
        return "콜라";
    }

}

public class Asdf {

    // static이 붙은 메소드는 클래스 메소드
    // 인스턴스를 만들지 않고 사용이 가능하다.
    // 인스턴스를 만들지 않아도 메모리에 올라가 있다.
    public static void main(String[] args) {

        // 인스턴스를 만드는 방법
        // 1. new 연산자와 생성자를 이용
        // 2. 클래스 로더를 이용
        // 3. 메모리에 있는 인스턴스를 복제

        // 인스턴스를 만들 때마다 메모리에 인스턴스가 생성된다.
        // 그러기 때문에 필요한 개수 만큼 생성해야 한다.
        // 메모리 관리 중요

        // 객체가 어떤 행동을 하는 이유일한 이유는 이 객체의 메소드를 다른 객체가 호출했을 때이다.

        VendingMachine vm1 = new VendingMachine();
        VendingMachine vm2 = new VendingMachine();

        String product = vm1.pushProductButton(100);

        System.out.println(product);



    }
}

```

```java
public class Student {

    // 필드(속성)
    String name;
    int age;
    String school;

    // 생성자
    public Student(String name, int age, String school) {
        this.name = name;
        this.age = age;
        this.school = school;
    }

    // 메서드
    public void introduce() {
        System.out.println("안녕하세요, 저는 " + name + "이고, " + age + "살입니다. " + school + "에 다니고 있습니다.");
    }

    public static void main(String[] args) {
        // Student 클래스의 인스턴스 생성
        Student student1 = new Student("Alice", 18, "ABC High School");
        Student student2 = new Student("Bob", 17, "XYZ High School");

        // 메서드 호출
        student1.introduce();
        student2.introduce();
    }
}
```
