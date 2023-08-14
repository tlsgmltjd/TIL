## Spring

- Java 애플리케이션 개발을 편하게 할 수 있게 해주는 JAVA 프레임워크이다.

```
https://start.spring.io/
```

---

### Controller

- MVC 패턴중 C이며 사용자의 요청을 처리한 후 지정된 뷰에 모델 객체를 넘겨주는 역할을 한다.

1. 웹 브라우저에 URI로 요청을 보내면 그 요청을 컨트롤러가 받게 된다.
2. 요청에 대한 응답을 반환한다.

#### @Controller(Spring MVC Controller)

- @Controller 어노테이션
- @GetMapping 어노테이션

> main/java/controller

```java
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HelloController {

    @GetMapping("hello") // /hello 경로로 접속 시
    public String hello() {
        return "hello";
    }
}
```

> main/resources/templates/hello.html

- Spring MVC는 뷰 리졸버를 사용하여 위의 html을 렌더링한다.

#### MVC와 템플릿 엔진

> Thymeleaf 탬플릿 엔진 사용

- @RequestParam 어노테이션

> main/java/controller

```java
@Controller
public class HelloController {

@GetMapping("hello-mvc")
public String helloMvc(@RequestParam(value = "name", required = false) String name, Model model) {
        model.addAttribute("name", name);
        return "hello-template";
    }
}
```

> resources/templates/hello-template.html

```html
<html xmlns:th="http://www.thymeleaf.org">
  <body>
    <p th:text="'hello ' + ${name}">hello! empty</p>
  </body>
</html>
```

#### API

- @ResponseBody 어노테이션

```java
@Controller
public class HelloController {

    @GetMapping("hello-string")
    @ResponseBody
    public String helloString(@RequestParam("name") String name) {
    return "hello " + name;
    }

}
```

- @ResponseBody 를 사용하면 뷰 리졸버( viewResolver )를 사용하지 않음
- 대신에 HTTP의 BODY에 문자 내용을 직접 반환

#### @ResponseBody 객체 반환 예시

```java
@Controller
public class HelloController {

    @GetMapping("hello-api")
    @ResponseBody
    public Hello helloApi(@RequestParam("name") String name) {
        Hello hello = new Hello();
        hello.setName(name);
        return hello;
    }

    static class Hello {
        private String name;

        // class 프로퍼티 접근방식
        // getter / seete 단축키 : ctrl + enter
        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }
    }
}
```

- viewResolver 대신에 HttpMessageConverter 가 동작

* 기본 문자처리: StringHttpMessageConverter
* 기본 객체처리: MappingJackson2HttpMessageConverter
