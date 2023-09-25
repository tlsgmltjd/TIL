## 정적 필드와 메서드

- 메모리에 한번 할당되어 프로그램이 종료될 때 해제되는 것을 의미한다.
- 항상 값이 변하지 않는다면 static을 사용해 메모리 낭비를 줄일 수 있다
- 객체를 생성하지 않고도 Static 자원에 접근이 가능하다

일반적으로 만든 **클래스는 static 영역**에 생성되고 new 연산을 통해 만든 **객체는 Heap 영역**에 생성된다.

Heap 영역의 메모리는 Garbage Collector 에 의해 수시로 관리 받는다.

하지만 static 영역에 할당된 메모리는 모든 객체가 공유하는 메모리라는 장점이 있지만 Garbage Collector의 관리 영역 밖이기 때문에 자주 난발한다면 시스템에 악영향을 주게된다.

```java
class Chicken {
    static String brand = "일수통닭";
    static String contact () {
        return "%s 점입니다.".formatted(brand);
    }

    static int lastNo = 0;

    int no;
    String name;

    public Chicken(String name) {
        no = ++lastNo;
        this.name = name;
    }

    String intro() {
        return "%s %호 %s 점입니다.".formatted(brand, no, name);
    }
}

public class Main {

    public static void main(String[] args) {

        // 클래스의 정적 메서드는 인스턴스를 생성하지 않고 사용가능
        String cBrandName = Chicken.brand;
        String cContact = Chicken.contact();

        Chicken s1 = new Chicken("광주");
        Chicken s2 = new Chicken("서울");
    }
}
```
