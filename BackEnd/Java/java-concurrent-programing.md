# 자바에서 동시성 프로그래밍

자바는 멀티 프로세싱과 멀티 스레딩 방식을 모두 지원하는 Concurrent 소프트웨어 개발이 가능한 언어이다.

## Thread, Runnable

자바에서는 스레드를 만들기 위해 Thread 클래스를 상속 받아 run 메서드를 구현해 생성하는 방식과 Runnable 함수형 인터페이스를 구현하고 Thread의 생성자로 넘겨 생성하는 방식이 있다.

```java
static class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread: " + Thread.currentThread().getName());
    }
}

public static void main(String[] args) {
    MyThread myThread = new MyThread();
    myThread.start();
}

---

Runnable task = () -> System.out.println("Thread: " + Thread.currentThread().getName());
Thread thread = new Thread(task);
thread.start();
```

### sleep, interrupt, join

- Thread.sleep()으로 스레드를 일정 시간 동안 정지시킬 수 있다.  
  Thread.interrupt를 실행해 스레드를 깨울 수 있다. (InterruptedExcpetion이 발생)  
  thread.join()으로 해당 스레드가 끝날 때 까지 현재 스레드를 대기시킬 수 있다.

## Executor

- Executor는 스레드를 직접 생성하지 않고 작업을 Runnable 또는 Callable로 정의하고 실행만 요청하는 방식이다.
- Executors 클래스를 사용해서 다양한 스레드 풀을 생성해 관리할 수 있다.
- Runnable의 리턴 타입은 void 타입, Callable은 제네릭(뒤에서 나올 Future<제네릭 타입> 이다.)으로 리턴 타입을 받을 수 있는 함수형 인터페이스다.

### Executors

- .newSingleThreadExecutor() -> 단일 스레드 익스큐터 생성
- .newFixedThredPool(int) -> 고정 개수의 스레드
- .newCachedThreadPool() -> 필요한 만큼 생성, 유휴 스레드는 제거
- .newScheduledThreadPool(int) -> 예약 실행이 가능한 스레드 풀

## Callable과 Future

Callable은 Runnanle과 다르게 제네릭 타입으로 결과를 반환하고 예외를 던진다. Future<T>는 Callable 작업의 결과를 담고, 아래와 같은 메서드를 제공한다.

- get() -> 결과를 대기 및 반환. blocking 한다.
- isDone() -> 작업 완료 여부 반환
- cancel() -> 작업 취소

### invokeAll / invokeAny

- Future.invokeAll(List<Callable>) -> 모든 작업 완료까지 대기, 각 결과는 Future로 반환
- Future.invokeAny(List<Callable>) -> 가장 빨리 끝난 하나의 작업 결과 반환. 결과는 Callable의 제네릭 타입

## CompletableFuture

CompletableFuture는 자바 8부터 도입된 비동기 프로그래밍 기술로, 명시적 콜백 등록과 체이닝이 가능하며, Future보다 편리한 API를 제공한다.

### 사용 방법

- .runAsync() -> 반환값 없음
- .supplyAsync() -> 반환값 있음

```java
CompletableFuture<Void> cf1 = CompletableFuture.runAsync(() -> System.out.println("작업 중"));
CompletableFuture<String> cf2 = CompletableFuture.supplyAsync(() -> "hi");
```

### 콜백

- .thenApply(Function) -> 결과를 가공하고 다음 콜백에서 소비한다
- .thenAccept(Cunsumer) -> 이전 결과 값을 받고 소비만 한다
- .thenRun(Runnable) -> 이전 결과 값을 받지 않고, 별도의 작업 실행

```java
cf2.thenApply(String::toLowerCase).thenAccept(System.out::println);
```

### 조합

- .thenCompose() -> 이전 결과를 기반으로 새 CompletableFuture 생성
- .thenCombine() -> 두 CompletableFuture를 병합

```java
cf2.thenCompose(msg -> CompletableFuture.supplyAsync(() -> msg + " WORLD"));
cf1.thenCombine(cf2, (a, b) -> a + b);
```

### 여러 작업 처리

- allOf() -> 모든 작업 완료 후 동작
- anyOf() -> 하나라도 완료 시 동작

```java
CompletableFuture<Void> all = CompletableFuture.allOf(cf1, cf2);
CompletableFuture<Object> any = CompletableFuture.anyOf(cf1, cf2);
```
