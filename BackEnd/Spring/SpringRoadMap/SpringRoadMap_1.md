## SpringRoadMap_1

> 감영한 스프링 로드맵 - 입문

### 비즈니스 요구사항 정리

- 데이터: 회원ID, 이름
- 기능: 회원 등록, 조회
- 아직 데이터 저장소가 선정되지 않음(가상의 시나리오)

일반적인 웹 애플리케이션 계층 구조

- **컨트롤러** : 웹 MVC의 컨트롤러 역할
- **서비스** : 핵심 비즈니스 로직 구현
- **리포지토리** : 데이터베이스에 접근, 도메인 객체를 DB에 저장하고 관리
- **도메인** : 비즈니스 도메인 객체
  - 회원, 주문, 쿠폰 등등 주로 데이터베이스에 저장하고 관리됨

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
