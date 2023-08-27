## API (Application Programming Interface)

- 컴퓨터 프로그램이 다른 프로그램과 상호작용하여 특정 기능을 수행을 위한 규칙과 규약을 정의한 인터페이스 이다.

**Public API** : 누구나 사용가능한 공개 API

**Peivate API** : 내부 API로 기업에서 자체 제품과 운영 개선을 위해 내부에서만 사용하는 API

**Partner API** : 동의하는 특정인들만 사용하는 API

---

### API 개발 단계

- API specification (명세)

### GET API

- HTTP Method -> GET
- HTTP Path -> /add
- 쿼리 -> int number1, int number2
- API의 응답 -> 숫자 - 두 숫자의 덧셈 결과

```java
@RestController // 아래의 클래스를 Controller로 등록한다.
public class CalCulatorController {

    @GetMapping("/add") // HTTP Method : GET /add
    public int addToNumbers(@RequestParam int number1, @RequestParam int number2) {
        return number1 + number2;
    }

}
```

`@RestController`

- 주어진 Class를 Controller로 등록한다.

`@GetMapping("/add")`

- 아래 함수를 HTTP Method가 GET이고 HTTP path가 /add인 API로 지정한다.

`@RequestParam`

- 주어지는 쿼리를 함수 파라미터에 넣는다.

```
/add?number1=10&number2=20
```

> 같은 이름을 가진 쿼리의 값이 들어온다.

### POST API

- HTTP Method -> POST
- HTTP Path -> /multiply
- HTTP Body (JSON)

```
  {
  "number1": 숫자,
  "number2": 숫자
  }
```

- API 응답 -> 숫자 (곱셈 결과)

```java
 @PostMapping("/multiply") // HTTP Method : POST /multiply
    public int multiplyTwoNumbers(@RequestBody CalculatorMultiplyRequest request) {
        return request.getNumber1() * request.getNumber2();
    }
```

`@RequestBody`

- HTTP Body로 들어오는 JSON을 주어진 객체로 변경해준다.
