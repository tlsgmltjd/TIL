## SpringRoadMap_1

> 감영한 스프링 로드맵 - 입문

### 비즈니스 요구사항 정리

- 데이터: 회원ID, 이름
- 기능: 회원 등록, 조회
- 아직 데이터 저장소가 선정되지 않음(가상의 시나리오)

일반적인 웹 애플리케이션 계층 구조

![](https://interesting-jackrabbit-80c.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d%2F7d5c32f6-780a-4160-bee8-609619eed69f%2F%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-09-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.16.53.png?table=block&id=7d21aad8-8272-4aa3-ae68-6211964a52b2&spaceId=3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d&width=1800&userId=&cache=v2)

- **컨트롤러** : 웹 MVC의 컨트롤러 역할
- **서비스** : 핵심 비즈니스 로직 구현
- **리포지토리** : 데이터베이스에 접근, 도메인 객체를 DB에 저장하고 관리
- **도메인** : 비즈니스 도메인 객체
  - 회원, 주문, 쿠폰 등등 주로 데이터베이스에 저장하고 관리됨

![](https://interesting-jackrabbit-80c.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d%2Ff0315498-a498-45fd-8751-eae7f8a2f51d%2F%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-09-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_6.19.33.png?table=block&id=6837810d-4982-4705-b14d-c71a79b25a5b&spaceId=3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d&width=1800&userId=&cache=v2)

```
MemberService -> MemberRepository(interface) <- - MemoryMemberRepository
```

- 아직 데이터 저장소가 선정되지 않아, 우선 인터페이스로 구현 클래스를 변경할 수 있도록 설계

**회원 객체**

```java
package hellospring.demo.domain;

public class Member {
private Long id;
private String name;

    public void setId(Long id) {
        this.id = id;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Long getId() {
        return id;
    }

    public String getName() {
        return name;
    }

}

```

**회원 리포지토리 인터페이스**

```java
package hellospring.demo.repository;

import hellospring.demo.domain.Member;
import org.springframework.stereotype.Repository;

import java.util.List;
import java.util.Optional;

public interface MemberRepository {
    Member save(Member member);
    Optional<Member> findById(Long id);
    Optional<Member> findByName(String name);
    List<Member> findAll();
}
```

**회원 리포지토리 메모리 구현체**

```java
package hellospring.demo.repository;

import hellospring.demo.domain.Member;
import org.springframework.stereotype.Repository;

import java.util.*;


public class MemoryMemberRepository implements MemberRepository{


    private static Map<Long, Member> store = new HashMap<>();
    private static long sequence = 0L;

    @Override
    public Member save(Member member) {
        member.setId(++sequence);
        store.put(member.getId(), member);
        return member;
    }

    @Override
    public Optional<Member> findById(Long id) {
        return Optional.ofNullable(store.get(id));
    }

    @Override
    public Optional<Member> findByName(String name) {
        return store.values().stream()
                .filter(member -> member.getName().equals(name))
                .findAny();
    }

    @Override
    public List<Member> findAll() {
        return new ArrayList<>(store.values());
    }

    public void clearStore() {
        store.clear();
    }
}
```

**회원 리포지토리 테스트 케이스 작성**

- 개발한 기능을 실행해서 테스트하는 방법은 준비하고 실행하는데 오래걸리고, 반복 실행하기 어렵고, 여러 테스트를 한번에 실행하기 어려운 단점이 있다.
- 자바는 JUnit이라는 프레임워크로 테스트를 실행할 수 있게 해준다.
- `@AfterEach` : 각 테스트 종료될 때마다 실행된다. 한번에 여러 테스트를 실행하면 메모리 DB에 직전 테스트의 결과가 남을 수 있다.

```java
public class MemoryMemberRepositoryTest {
    MemoryMemberRepository repository = new MemoryMemberRepository();

    @AfterEach
    public void afterEach() {
        repository.clearStore();
    }

    @Test
    public void save() {
        // given
        Member member = new Member();
        member.setName("spring");

        // when
        repository.save(member);

        // then
        Member result = repository.findById(member.getId()).get();
        Assertions.assertThat(member).isEqualTo(result);
    }

    @Test
    public void findByName() {
        // given
        Member member1 = new Member();
        member1.setName("spring1");
        repository.save(member1);

        Member member2 = new Member();
        member2.setName("spring2");
        repository.save(member2);

        // when
        Member result = repository.findByName(member1.getName()).get();

        // then
        Assertions.assertThat(result).isEqualTo(member1);
    }

    @Test
    public void findAll() {
        // given
        Member member1 = new Member();
        member1.setName("spring1");
        repository.save(member1);

        Member member2 = new Member();
        member2.setName("spring2");
        repository.save(member2);

        // when
        List<Member> result =  repository.findAll();

        // then
        Assertions.assertThat(result.size()).isEqualTo(2);
    }
}
```

**회원 서비스**

```java
@Service
public class MemberService {
    private final MemberRepository memberRepository = new MemoryMemberRepository();

    /*
    * 회원가입
    * */
    public Long join(Member memebr) {
        // 같은 이름이 있는 중복 회원 X
        validataDuplicateMember(memebr); // 중복 회원 검증
        memberRepository.save(memebr);
        return memebr.getId();
    }

    private void validataDuplicateMember(Member memebr) {
        memberRepository.findByName(memebr.getName())
                .ifPresent(m -> {
                    throw new IllegalStateException("이미 존재하는 회원입니다.");
                 });
    }

    /*
    * 전체 회원 조회
    * */
    public List<Member> findMembers() {
        return memberRepository.findAll();
    }

    /*
     * 특정 회원 조회
     * */
    public Optional<Member> findOne(Long memberId) {
        return memberRepository.findById(memberId);
    }


}
```

- 회원 서비스 코드를 DI를 가능하게 변경한다.

```java
private final MemberRepository memberRepository;

public MemberService(MemberRepository memberRepository) {
    this.memberRepository = memberRepository;
}
```

**회원 서비스 테스트 코드**

- `@BeforeEach` : 각 테스트 실행 전에 호출된다. 테스트가 서로 영향이 없도록 항상 새로운 객체를 생성하고, 의존관계도 새로 맺어주는 역할을 한다.

```java
...

    MemberService memberService;
    MemoryMemberRepository memberRepository;

    @BeforeEach
    public void beforeEach() {
        memberRepository = new MemoryMemberRepository();
        memberService = new MemberService(memberRepository);
    }

    @AfterEach
    public void afterEach() {
        memberRepository.clearStore();
    }

    @Test
    void 회원가입() {
        // given <- 이러한 상황이 주어져서
        Member member = new Member();
        member.setName("hello");

        // when <- 이걸 실행 했을 떄
        Long saveId = memberService.join(member);

        // then <- 이게 나와야해
        Member findMember = memberService.findOne(saveId).get();
        Assertions.assertThat(findMember.getName()).isEqualTo(member.getName());
    }

...
```

**회원 컨트롤러에 의존관계 추가**

```java
@Controller
public class MemberController {
    private final MemberService memberService;

    @Autowired
    public MemberController(MemberService memberService) {
        this.memberService = memberService;
    }
}
```

- 생성자에 `@Autowired` 가 있으면 스프링이 연관된 객체를 스프링 컨테이너에서 찾아서 넣어준다. DI

- 다음 어노테이션은 스프링 빈으로 자동 등록해준다.
- @Conponent
- @Controller
- @Service
- @Repository

**DI를 할 수 있도록 MemberService, MemoryMemeberRepository 를 스프링 빈으로 등록해준다.**

```java
@Controller
public class MemberController {
    private final MemberService memberService;

    @Autowired
    public MemberController(MemberService memberService) {
        this.memberService = memberService;
    }
}
```

```java
@Service
public class MemberService {
    private final MemberRepository memberRepository;

    public MemberService(MemberRepository memberRepository) {
        this.memberRepository = memberRepository;
    }

...
}
```

```java
@Repository
public class MemoryMemberRepository implements MemberRepository{ ... }
```

**직접 스프링 빈에 등록하는법**

```java
// 직접 스프링 빈에 등록
@Configuration
public class SpringConfig {

    @Bean
    public MemberService memberService() {
        return new MemberService(memberRepository());
    }

    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository();
    }
}
```

> DI 방법 : **생성자 주입(권장), setter 주입, 필드 주입**

**MVC**

![](https://interesting-jackrabbit-80c.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d%2Ff7b65b5a-eeae-4505-a681-1f62d5880716%2F%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-09-21_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_11.07.23.png?table=block&id=06b0e076-8751-410a-adbf-21b3e6906cb3&spaceId=3ad1f604-bb8b-4a0c-8d3a-aab5c473bf7d&width=1800&userId=&cache=v2)

- (@Controller) 요청이 오면 스프링 컨트롤러가 있는지 확인 후 static 파일을 찾는다.

```java
@Controller
public class HomeController {
    @GetMapping("/")
    public String home() {
        return "home";
    }
}

// resourse/templates/home.html
```

```java
public class MemberController {
    private final MemberService memberService;

    @Autowired
    public MemberController(MemberService memberService) {
        this.memberService = memberService;
    }

    @GetMapping("/members/new")
    public String createForm() {
        return "members/createMemberForm";
    }
    @PostMapping("/members/new")
    public String create(MemberForm form) {
        Member member = new Member();
        member.setName(form.getName());
        memberService.join(member);
        return "redirect:/";
    }
}
```

```java
public class MemberForm {
    private String name;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

- `/` -회원등록→ `members/new` -폼 데이터 입력→ `members/new` POST요청 (body = name: string) → Member 객체 생성 → 데이터 추가 → MemberService.join() 메서드로 Member 객체 저장

```java
@GetMapping("/members")
    public String list(Model model) {
        List<Member> members = memberService.findMembers();
        model.addAttribute("members", members);
        return "members/memberList";
    }
```

**회원 조회 기능**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
  <body>
    <div class="container">
      <div>
        <table>
          <thead>
            <tr>
              <th>#</th>
              <th>이름</th>
            </tr>
          </thead>
          <tbody>
            <tr th:each="member : ${members}">
              <td th:text="${member.id}"></td>
              <td th:text="${member.name}"></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <!-- /container -->
  </body>
</html>
```

---

## JDBC

- 디비에 쉽게 접근할 수 있도록 도와주는 자바의 API 이다.

```
implementation 'org.springframework.boot:spring-boot-starter-jdbc'
```

> JDBC API롤 직접 코딩하는 것은 20년 전의 이야기 이므로, 참고만 하고 넘어가자

JdbcMemberRepository를 만들어서 MemberRepository를 구현하게 한다.

```java

public class JdbcMemberRepository implements MemberRepository {
    private final DataSource dataSource;

    public JdbcMemberRepository(DataSource dataSource) {
        this.dataSource = dataSource;

    }

    @Override
    public Member save(Member member) {
        String sql = "insert into member(name) values(?)";

        Connection conn = null;
        PreparedStatement pstmt = null;
        ResultSet rs = null;
        try {
            conn = getConnection();
            pstmt = conn.prepareStatement(sql,
                    Statement.RETURN_GENERATED_KEYS);
            pstmt.setString(1, member.getName());

            pstmt.executeUpdate();
            rs = pstmt.getGeneratedKeys();

            if (rs.next()) {
                member.setId(rs.getLong(1));
            } else {
                throw new SQLException("id 조회 실패");
            }
            return member;
        } catch (Exception e) {
            throw new IllegalStateException(e);
        } finally {
            close(conn, pstmt, rs);
        }
    }

    @Override
    public Optional<Member> findById(Long id) {
        String sql = "select * from member where id = ?";
        Connection conn = null;
        PreparedStatement pstmt = null;

        ResultSet rs = null;
        try {
            conn = getConnection();
            pstmt = conn.prepareStatement(sql);
            pstmt.setLong(1, id);
            rs = pstmt.executeQuery();
            if (rs.next()) {
                Member member = new Member();
                member.setId(rs.getLong("id"));
                member.setName(rs.getString("name"));
                return Optional.of(member);
            } else {
                return Optional.empty();
            }
        } catch (Exception e) {
            throw new IllegalStateException(e);
        } finally {
            close(conn, pstmt, rs);
        }
    }

    @Override
    public List<Member> findAll() {
        String sql = "select * from member";
        Connection conn = null;
        PreparedStatement pstmt = null;
        ResultSet rs = null;
        try {
            conn = getConnection();
            pstmt = conn.prepareStatement(sql);
            rs = pstmt.executeQuery();

            List<Member> members = new ArrayList<>();
            while (rs.next()) {
                Member member = new Member();
                member.setId(rs.getLong("id"));
                member.setName(rs.getString("name"));
                members.add(member);
            }
            return members;
        } catch (Exception e) {
            throw new IllegalStateException(e);
        } finally {
            close(conn, pstmt, rs);
        }
    }

    @Override
    public Optional<Member> findByName(String name) {
        String sql = "select * from member where name = ?";
        Connection conn = null;
        PreparedStatement pstmt = null;
        ResultSet rs = null;
        try {
            conn = getConnection();
            pstmt = conn.prepareStatement(sql);
            pstmt.setString(1, name);
            rs = pstmt.executeQuery();
            if (rs.next()) {
                Member member = new Member();
                member.setId(rs.getLong("id"));
                member.setName(rs.getString("name"));
                return Optional.of(member);
            }

            return Optional.empty();
        } catch (Exception e) {
            throw new IllegalStateException(e);
        } finally {
            close(conn, pstmt, rs);
        }
    }

    private Connection getConnection() {
        return DataSourceUtils.getConnection(dataSource);
    }

    private void close(Connection conn, PreparedStatement pstmt, ResultSet rs) {
        try {
            if (rs != null) {
                rs.close();
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
        try {
            if (pstmt != null) {
                pstmt.close();
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
        try {
            if (conn != null) {
                close(conn);
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private void close(Connection conn) throws SQLException {
        DataSourceUtils.releaseConnection(conn, dataSource);
    }
}

```

- DataSource 는 디비의 커넥션을 획득할 때 사용하는 객체이다.
- 스프링은 디비의 커넥션 정보를 바탕으로 DataSource를 생성하고 스프링 빈으로 만들어 저장한다.

이렇게 JdbcMemberRepository를 스프링 빈에 등록 시켜준다.

```java
@Configuration
public class SpringConfig {

    private final DataSource dataSource;

    @Autowired
    public SpringConfig(DataSource dataSource) {
        this.dataSource = dataSource;
    }

    @Bean
    public MemberService memberService() {
        return new MemberService(memberRepository());
    }

    @Bean
    public MemberRepository memberRepository() {
//        return new MemoryMemberRepository();
        return new JdbcMemberRepository(dataSource);
    }
}
```

- 이렇게하면 서비스 로직은 전혀 건들이지 않고 메모리 저장 방식에서 디비 저장 방식으로 레포지토리를 변경했다.

```
MemberService -> <interface>MemberRepository <- JdbcMemberRepository
```

- 개방-폐쇄 원칙 (OCP)
  - 모듈의 확장성을 보장하지만 객체를 직접적으로 수정하는 것을 제한한다는 의미이다.
  - 추상화를 의미한다.
- DI를 사용하여 기존 코드를 변경하지 않고 구현체를 변경하였다.
- 다형성이 구현된다!
