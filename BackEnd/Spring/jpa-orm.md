# Spring Data JPA와 ORM

## ORM

> Object-Relational Mapping

- 자바의 객체와 관계형 데이터베이스가 1 : 1 로 매핑되는 것이다.
- 복잡한 SQL 쿼리가 아닌 직관적인 코드로 데이터베이스를 조작할 수 있다.

```sql
create table student
(
    id bigint auto_increment,
    name varchar(255),
);
```

```java
public class Student {
    private Long id;
    private String name;
}
```

- 이렇게 객체와 테이블을 매핑해주는 것이 ORM이다.
- 객체와 테이블이 매핑되어있어, ORM을 사용하여 복잡한 쿼리를 날리는 대신 간결한 코드로 데이터를 다룰 수 있다.

* ORM에는 대표적으로 Hibernate, myBatis가 있다.

## JPA

> Java Persistence API

- Persistence : 영속성
  - 서버가 재시작되어도 데이터는 영구적으로 저장되는 속성이다.
- JPA는 자바 객체와 DB 테이블을 1 : 1 매핑 처리하기 위한 ORM표준이다.
  - 인터페이시의 집합.

### Hibernate

- JPA의 구현체 중 하나이다.
- 내부적으로 JDBC를 사용한다.

```sql
JPA(interface) <-(구현)- Hibernate -(사용)-> JDBC
```

### Spring Data JPA

- JPA를 한 단계 더 추상화 시킨 인터페이스(repository)이다.
- CRUD 처리를 위한 인터페이스 제공
- 개발시 인터페이스만 작성하면 실행 시 나머지 과정은 JPA가 알아서 해줌
- 제공하는 인터페이스인 Repository를 생성한 후 정해준 규칙대로 메서드를 정이하여 사용하면,
  알아서 해당 메서드의 이름을 보고 쿼리를 날리는 구현체를 만들어 Bean에 등록한다.
  > ex.

```java
public interface UserRepository extends JpaRepository<User, Long> {
  Optional<UserEntity> findByName(String name);
}
```

---

```
Applicarion <-> Spring Data JPA <-> JPA <-> Hibernate <-> JDBC <-> RDB
```
