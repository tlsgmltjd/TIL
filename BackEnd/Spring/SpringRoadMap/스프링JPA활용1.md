## SpringJpaRoadMap 2-2

> 김영한 - 스프링 Jpa 로드맵 - JPA 활용 1편

## 예제 도메인 분석

![](https://interesting-jackrabbit-80c.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d%2Ff86cacea-e6aa-4c50-81d9-99141d673b77%2FUntitled.png?table=block&id=1d47d6c8-cc27-4d48-ad18-2160c7346cbf&spaceId=3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d&width=2000&userId=&cache=v2)

해당 서비스의 도메인 모델과 테이블이다.

회원은 여러개의 주문을 가질 수 있고(1:N) 주문은 여러개의 상품을 가질 수 있고 상품도 여러개의 주문을 가질 수 있기 때문에 N:N 연관관계이다.

N:N 연관관계는 관계형 데이터베이스에서 사용하는 것은 권장되지 않으므로 주문상품이라는 엔티티를 추가하여 1:N, N:1로 풀어냈다.

왜? @ManyToMany 를 사용하여 N:N 매핑시 아래와 같이 JPA에서 자동으로 중간 테이블을 만들어서 처리 해준다.

---

| Member        |
| ------------- |
| member_id(PK) |
| member_name   |

> @JoingTable을 사용하여 만든 중간테이블

| Order             |
| ----------------- |
| member_id(PK), FK |
| item_id(PK, FK)   |

| Item        |
| ----------- |
| item_id(PK) |
| item_name   |

---

이렇게 만들어진 중간 테이블에서는 매핑에 필요한 정보들만 담겨있지 비즈니스 로직상 필요한 컬럼들은 들어있지 않다. (언제 주문 했는지 같은 정보들)

따라서 실무에서는 N:N 연관관계 사용을 권장하지 않고, 필요에 따라 N:1, 1:N 연관관계를 만들어서 풀어줘야한다.

## ![](https://interesting-jackrabbit-80c.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d%2F3b37ca08-25af-4786-aabc-5771fe41bd0f%2F%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2024-01-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.33.39.png?table=block&id=746b8f61-9276-4396-a27b-9f36b4dd18e8&spaceId=3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d&width=2000&userId=&cache=v2)

## 엔티티

### 회원 엔티티

```java
@Entity
@Data
public class Member {
    @Id @GeneratedValue
    @Column(name = "member_id")
    private Long id;

    private String name;

    @Embedded
    private Address address;

    @OneToMany(mappedBy = "member")
    private List<Order> orders = new ArrayList<>();
}
```

한 회원은 여러개의 주문을 갖는다.

컬렉션 필드는 바로바로 초기화 하는 것이 안전하다. null문제에서 안전할 수 있고, 하이버네이트는 영속화 할때 컬렉션을 감싸서 하이버네이트가 제공하는 내장 컬렉션으로 변경한다. 컬력션을 변경한다면 문제가 생긴다.

### 주문

```java
@Entity
@Table(name = "orders")
@Data
@NoArgsConstructor(access = PROTECTED)
public class Order {
    @Id @GeneratedValue
    @Column(name = "order_id")
    private Long id;

    @ManyToOne
    @JoinColumn(name = "member_id")
    private Member member;

    @OneToMany(mappedBy = "order", cascade = ALL)
    private List<OrderItem> orderItems = new ArrayList<>();

    @OneToOne(fetch = LAZY, cascade = ALL)
    @JoinColumn(name = "delivery_id")
    private Delivery delivery;

    private LocalDateTime orderDate;

    @Enumerated(EnumType.STRING)
    private OrderStatus status;

    // ...
}
```

주문은 여러개의 주문 아이템(중간 테이블)을 갖는다.

### 주문 상태

```java
public enum OrderStatus {
    ORDER, CANCEL
}
```

### 주문 상품

```java
@Entity
@Data
@NoArgsConstructor(access = PROTECTED)
public class OrderItem {
    @Id @GeneratedValue
    @Column(name = "order_item_id")
    private Long id;

    @ManyToOne(fetch = LAZY)
    @JoinColumn(name = "item_id")
    private Item item;

    @ManyToOne(fetch = LAZY)
    @JoinColumn(name = "order_id")
    private Order order;

    private Integer orderPrice;

    private Integer count;

    // ...
}
```

중간 테이블이며 여러개의 아이템과 여러개의 주문을 갖는다.

### 아이템

```java
@Entity
@Data
@Inheritance(strategy = InheritanceType.SINGLE_TABLE)
@DiscriminatorColumn(name = "dtype")
public abstract class Item {
    @Id @GeneratedValue
    @Column(name = "item_id")
    private Long id;

    private String name;

    private Integer price;

    private Integer stockQuantity;

    @ManyToMany(mappedBy = "items")
    private List<Category> categories = new ArrayList<>();
}
```

아이템 클래스를 상속 받아 다양한 종류의 아이템을 만들었다.

해당 엔티티는 한 테이블에 모든 아이템 종류의 컬럼이 들어가고 `dtype` 이라는 컬럼의 값으로 어떤 아이템인지 식별할 수 있다.

```java
@Entity
@DiscriminatorValue("B")
@Getter @Setter
public class Book extends Item {
    private String author;
    private String isbn;
}
```

```java
@Entity
@DiscriminatorValue("A")
@Getter @Setter
public class Album extends Item {
    private String artist;
    private String etc;
}
```

```java
 @Entity
@DiscriminatorValue("M")
@Getter @Setter
public class Movie extends Item {
    private String director;
    private String actor;
}
```

### 카테고리

```java
@Entity
@Data
public class Category {
    @Id @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "category_id")
    private Long id;

    private String name;

    @ManyToMany
    @JoinTable(name = "category_item",
            joinColumns = @JoinColumn(name = "category_id"),
            inverseJoinColumns = @JoinColumn(name = "item_id"))
    private List<Item> items = new ArrayList<>();

    @ManyToOne(fetch = LAZY)
    @JoinColumn(name = "parent_id")
    private Category parent;

    @OneToMany(mappedBy = "parent")
    private List<Category> child = new ArrayList<>();

    // ...
}
```

### 주소 값 타입

```java
@Embeddable
@Getter
@AllArgsConstructor
@NoArgsConstructor
public class Address {
    private String city;
    private String street;
    private String zipcode;
}
```

값 타입은 변경 불가능하게 설계해야한다.

기본 생성자를 두는 것도 `protected` 로 설정하는 편이 안전하다 (다른 곳에서 생성할 수 없게)

> 생성자가 있어야하는 이유는 자바 리플렉션같은 기술을 사용할 수 있도록 지원해야하기 때문이다.

<br />

**모든 연관관계는 지연로딩으로 설정해야한다.**

- 즉시 로딩은 예측이 어렵고 어떤 SQL 쿼리가 날라갈 지 추적하기 어렵다. JPQL을 실행할 때 N+1 문제가 자주 발생한다.

즉시 로딩은 데이터를 조회할 때 연관된 데이터까지 한꺼번에 모두 불러오는 것이고, 지연 로딩은 필요한 시점에 연관된 데이터를 불러오는 것이다.

N+1 문제는 1은 최소 쿼리, N은 최소 쿼리의 결과 개수이다. 최소 1번 쿼리했는데 그 결과 개수만큼 추가적인 쿼리가 나가는 무시무시한 문제이다.

예를 들어 Member와 1:N 관계인 Team 엔티티들이 있다고 가정을 하고, 10명의 Member 불러오는 JPQL 쿼리를 날린다면  
Member 10명을 조회하는 쿼리 1개와 각각 Team을 조회하는 쿼리가 10개가 날라간다..

---

## 요구사항 분석

**쇼핑몰 프로젝트**

- 회원 기능
  - 회원 등록
  - 회원 조회
- 상품 기능
  - 상품 등록
  - 상품 수정
  - 상품 조회
- 주문 기능
  - 상품 주문
  - 주문 내역 조회
  - 주문 취소
- 기타 요구사항
  - 상품은 재고 관리가 필요함
  - 상품의 종류는 도서, 음반, 영화가 있다
  - 상품을 카테고리로 구분할 수 있다
  - 상품 주문시 배송 정보를 입력할 수 있다

## 회원

### 회원 Repository

```java
@Repository
public class MemberRepository {
    @PersistenceContext
    private EntityManager em;

    public void save(Member member) {
        em.persist(member);
    }

    public Member findById(Long id) {
        return em.find(Member.class, id);
    }

    public List<Member> findAll() {
        // JPQL
        return em.createQuery("SELECT m FROM Member m", Member.class)
                .getResultList();
    }

    public List<Member> findByName(String name) {
        return em.createQuery("SELECT m FROM Member m WHERE m.name = :name", Member.class)
                .setParameter("name", name)
                .getResultList();
    }
}
```

`@PersistenceContext` 어노테이션으로 EntityManager을 주입받을 수 있다.

`em.persit()` 으로 엔티티를 영속화할 수 있다.

`em.find(Entity.class, PK)` 로 엔티티를 PK로 조회할 수 있다.

`em.createQuery(sql, Entity.class)` 로 JPQL 쿼리를 직접 작성할 수 있다.

- `.getResultList()` 로 결과 값을 List 형태로 반환 받을 수 있ㄷ.
- `.setParameter()` 로 쿼리에 값을 넣어 조회할 수 있다.

### 회원 Service

```java
@Service
@Transactional(readOnly = true)
@RequiredArgsConstructor
public class MemberService {
    private final MemberRepository memberRepository;

    /**
     * 회원 가입
     */
    @Transactional
    public Long join(Member member) {
        validateDuplicateMember(member); // 중복 회원 검증
        memberRepository.save(member);
        return member.getId();
    }

    private void validateDuplicateMember(Member member) {
        List<Member> members = memberRepository.findByName(member.getName());
        if (!members.isEmpty()) {
            throw new IllegalStateException("이미 존재하는 회원입니다.");
        }
    }

    /**
     * 회원 전체 조회
     */
    public List<Member> findMembers() {
        return memberRepository.findAll();
    }


    /**
     * 회원 단건 조회
     */
    public Member findById(Long id) {
        return memberRepository.findById(id);
    }
}
```

MemberRepository 를 주업하는 것처럼 DI를 할땐 생성자 주압하는 것이 좋다.  
왜냐하면 생성 시점에 뭘 의존하고 있는지 표현할 수 있다.

`@Transactional` 어노테이션은 스프링에서 제공하는 어노테이션을 사용하는 것이 좋다. (쓸 수 있는 옵션이 많다.)
