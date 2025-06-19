# 자바에서 동시성 문제 해결 방법

## synchronized

- synchronized 키워드를 선언한 블럭은 cricical section이 되며, 동시에 하나의 스레드만 접근할 수 있게 된다.
- 자바의 모든 객체들은 모니터를 가지고 있으며, synchronized 키워드를 선언한다면, 임계 구역 객체에 오직 하나의 스레드만 접근할 수 있게 보장한다.
- 각 객체마다 하나의 모니터를 갖고 있기 때문에, synchronized 키워드가 선언된 메서드 하나만 실행 중이여도, 같은 객체의 synchronized 메서드들은 모두 락이 걸린다.

```java
public class Main {
    public synchronized void test() {
        // 동시성 처리가 중요한 로직들..
    }
}
```

## volatile

- 기본적으로 자바의 스레드는 OS 단의 CPU 캐시 메모리를 복사해 사용한다. 하지만 CPU 캐시의 데이터가 메인 메모리(RAM)에 반영되는 시점은 예측하기 어렵기 때문에, 스레드 간 동기화 문제가 발생할 수 있다. 이때 volatile 키워드를 붙히면 CPU캐시가 아닌 메인 메모리에서 값을 참조한다.
- volatile 키워드는 한 개의 스레드가 변수에 쓰기(write)만 하고, 다른 스레드들이 읽기(read)만 하는 상황에서 가시성과 안정성이 보장된다. 즉, volatile은 변수 값이 CPU 캐시에 머무르지 않고, 항상 메인 메모리(RAM)에서 읽히도록 보장한다. 다만, 원자성은 보장하지 않기 때문에 연산 작업에 대한 원자성 보장은 되지 않는다.

```java
public class Main {
    private volatile int count = 0;

    // ..
}
```

## Atomic Type

- 연산에 대한 원자성을 보장하는 타입이다.
- synchronized 키워드로 동시성 제어를 한다면 blocking 하게 동작하여 처리량이 낮지만, Atomic Tpye을 사용하면 non-blocking 하게 동작해 높은 처리량으로 원자성을 보장할 수 있다.
- 내부적으로 CAS(Compared And Swap) 알고리즘을 사용하여 non-blocking 하게 동작할 수 있다.

```java
public class Main {

    private static AtomicInteger count = new AtomicInteger(0);

    public void test() {
        count.incrementAndGet(); // 원자적 연산
    }
}
```

### CAS 알고리즘

- 인자로 기존 값과 변경할 값을 전달한다.
- 기존 값이 현재 메모리가 가지고 있는 값과 동일하다면, 변경할 값을 반영하고 true를 리턴한다.
- 만약 동일하지 않다면, 값을 반영하지 않고 false를 리턴한다.

* 특정 스레드에서 공유 자원에 대한 연산을 마치고, 메모리에 반영하기 직전에 다른 스레드가 공유 자원의 값을 변경한 상황에서는 값을 반영하면 안된다.
  - 이런 상황에 값을 반영하지 않고 false를 리턴하고, 변경된 값을 다시 읽고 재연산을 진행한다.
