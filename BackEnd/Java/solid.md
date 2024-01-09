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

- LSP 원칙은 서브 타입은 언제나 부모

## ISP 인터페이스 분리 원칙

> Interface Segregation Principle

## DIP 의존 역전 원칙

> Dependency Inversion Principle
