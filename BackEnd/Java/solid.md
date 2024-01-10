# SOLID 원칙

> 객체 지향의 설계의 5가지 원칙

- **S**RP Single Responsibility Principle | 단일 책임 원칙
- **O**CP Open Closed Priciple | 개방 폐쇄 원칙
- **L**SP Listov Substitution Priciple | 리스코프 치환 원칙
- **I**SP Interface Segregation Principle | 인터페이스 분리 원칙
- **D**IP Dependency Inversion Principle | 의존 역전 원칙

## SRP 단일 책임 원칙

> Single Responsibility Principle

- 한 클래스는 하나의 책임만 가져야 한다.

하나의 클래스는 하나의 기능을 담당하여 하나의 기능을 수행해야한다.

하나의 클래스에 많은 책임이 있다면 변경이 일어났을 때 영향을 끼치는 코드가 많아진다.

SRP 원칙을 따름으로써 한 책임의 변경으로부터 다른 책임의 변경이 일어나는 연쇄작용을 막을 수 있다.

## OCP 계방 폐쇄 원칙

> Open Closed Principle

- 확장에는 열려있어야 하며, 수정에는 닫혀있어야한다.

기능 추가가 필요하면 클래스를 확장하여 구현하고, 확장에 따른 클래스의 수정은 최소화 해야한다.

## LSP 리스코프 치환 원칙

> Liskov Substitution Principle

- LSP 원칙은 자식 타입은 항상 부모 타입으로 교체할 수 있어야한다는 원칙이다.

다형성의 특징을 이용하기 위해 부모 타입으로 자식 클래스를 선언하여 부모의 메서드를 사용해도 동작이 잘 되어야 한다.

예시로 컬렉션즈 프레임워크를 들 수 있다.

```java
Collection data = new ArrayList();
data = new HashSet();

data.add(1);
```

이렇게 자식 타입은 언제나 부모 타입으로 교체할 수 있어야 한다는 것을 의미한다.

## ISP 인터페이스 분리 원칙

> Interface Segregation Principle

- 인터페이스를 각각 사용 용도에 맞게 잘 분리하여 설계해야한다는 원칙이다.

SRP가 클래스의 단일 책임 원칙을 강조한다면, ISP는 인터페이스의 단일 책임을 강조하는 것이다.

한번 인터페이스를 분리해놓고 나중에 수정사항이 생겨 인터페이스들을 분리하는 행위를 하면 안된다.

> 한번 구성했으면 왠만하면 변하지 않아야한다.

## DIP 의존 역전 원칙

> Dependency Inversion Principle

- 어떤 클래스를 참조해야 할 때 그 클래스를 직접 참조하는 것이 아니라 대상의 상위 요소로 참조하라는 원칙이다.
  > 구현 클래스가 아닌 인터페이스에 의존하라는 의미이다.

의존 관계를 맺을 땐 변화하기 쉬운 것, 자주 변하는 것보다는 변화하기 어려운 것, 거의 변화가 없는 것에 의존하라는 것이다.

이러면 결합도를 낮출 수 있다.
