# 웹 개발

---

## 웹

- **WWW(World Wide Web)** 인터넷이 연결된 전세계 사람들이 서로 정보를 공유하는 장소이다.

## 웹 개발자

### 프론트엔드 개발자

- 프론트엔드 개발자는 UI / UX 를 개발한다.  
  **HTML CSS JavaScript** 등을 다양한 기술스택을사용하여 웹 페이지 디자인과 기능을 구현한다.

### 백엔드 개발자

- 백엔드 개발자는 사용자가 필요로 하는 **정보를 저장 및 관리하고, 전달**하는 영역을 담당한다.  
  주로 Java, Python, Node.js 등 다양한 프로그래밍 언어를 사용하여 서버 로직을 구현한다.

### 풀스택 개발자

- 풀스택 개발자는 **프론트엔드와 백엔드** 모두를 다룰 수 있는 개발자 이다.  
   즉, **클라이언트-서버 모든 분야에 걸친 개발 지식**을 가진 개발자이기 때문에  
   팀 내에서 빈틈없는 협업이 가능하다.

### DevOps 엔지니어

- DevOps는 Development + Operations 개발과 운영의 합성어이다.  
  DevOps는 개발자와 운영자가 함께 일하는 것을 돕고,  
  배포 과정을 자동화하여 소프트웨어를 안정적으로 배포하도록 돕는 것입니다.

### 프로젝트 매니저

- 프로젝트 매니저는 웹 개발 프로젝트를 계획, 실행, 모니터링 및 평가하는 역할을 이다. 즉, 프로젝트 매니저는 소프트웨어 개발 라이프사이클 전반에 걸쳐 프로젝트를 이끄는 일을 한다.

---

## 프론트엔드와 백엔드의 개념 및 차이점

##### - 프론트엔드는 사용자가 직접 사용하는 웹 페이지의 인터페이스를 개발하는 분야이다. <br />HTML, CSS, JavaScript 등을 사용하여 웹 사이트의 레이아웃, 디자인, 동작 등을 개발한다.

##### - 백엔드는 사용자가 볼 수 없는 서버 측 기능을 개발하는 분야이다. <br />서버 측에서 데이터베이스, 웹 서버를 개발하고, 프론트엔드와 데이터베이스를 연동하여 동작한다.

#### 프론트엔드와 백엔드는 기능적으로 다르지만, 서로 상호작용하여 웹 애플리케이션을 개발한다.

## git flow란?

- git flow는 브랜치 관리 전략 중 하나이다.

1. 개발을 할 때는 `develop` 브랜치를 만들어 해당 브랜치에서 개발을 한다.
2. `develop` 브랜치에서 특정 기능을 개발할 때는 `feature` 브랜치를 생성하여 개발을 한다.
3. `feature` 브랜치의 개발이 끝나면 `develop` 브랜치로 pull request 후, merge를 한다.

- 필요가 없어진 `feature` 브랜치는 삭제한다.

4. `develop` 브랜치에서 어느정도 개발이 완료된다면 `release` 브랜치를 생성하여 QA를 진행한다.
5. QA를 통과한다면 `master` 와 `develop` 브랜치로 merge한다.

---

## Code review?

- 개발 과정에서 다른 개발자나 팀원 등이 작성한 코드를 검토하고 분석하는 과정이다.

#### 사용해야하는 이유?

- 다른 개발자들이 코드를 검토하고 피드백을 주면서, 코드의 품질을 향상시킬 수 있으며 여러 잠재적인 버그를 찾고 수정할 수 있다.

## branch rule?

- 깃을 이용한 공동 작업에서 각각의 브랜치에서 어떤 작업을 해야 하는지에 대한 규칙이다.

#### 사용해야하는 이유?

- 예를 들어 **프랜치 명칙 규칙**을 정하여 이를 통해 개발자들은 어떤 브랜치에서 작업 중인지 쉽게 파악할 수 있다. 이처럼 branch rule을 사용하면 브랜치를 일관성 있게 사용할 수 있고, 개발 작업의 효율성을 높일 수 있습니다.

---

### 내가 하고싶은 전공

`프론트 엔드` 개발자이다.

### 왜?

- 프론트 엔드 개발자는 UI 를 개발하는 역할이다. 이는 디자인과 밀접한 관련이 있고 빠르게 결과물을 확일 할 수 있기 때문에 매력을 느꼈다. <br />
  그리고 (UX) 사용자 경험을 개선하여 사용자들이 보다 쉽게 웹 사이트를 사용할 수 있게 하는 것이 마음에 들었다.

---

## 프레임 워크와 라이브러리

### 개념

**프레임 워크**

- 프레임워크는 소프트웨어 개발에 필요한 **구조와 규칙을 제공하는 일종의 체계**이다.  
  쉽게 말해 집을 짓는 철근과 콘크리트 구조물과 같이 소프트웨어 개발을 위한 전체적인 구조와 규칙을 제공한다!  
  개발자는 이 구조를 따라 소프트웨어를 개발하며, 프레임워크는 이를 기반으로 필요한 코드를 생성하고 관리한다.

**라이브러리**

- 라이브러리는 개발자가 코드를 작성할 때 **유용한 함수, 클래스, 인터페이스** 등을 제공하는 소프트웨어 모음이다.  
  쉽게 말해 도구 상자와 같이, 개발자가 필요한 도구를 가져다 쓰는 역할이다.

### 차이점

- 라이브러리와 프레임워크의 차이는 제어 흐름에 대한 주도성이 누구에게 있는가에 있다.  
  즉,  
  **프레임워크**는 전체적인 흐름을 자체적으로 가지고 있으며, 프로그래머가 그 안에 필요한 코드를 작성한다.  
  **라이브러리**는 사용자가 흐름에 대해 제어를 하며 필요한 상황에 가져다 쓰는 것이다.

---

## API?

- API는 프로그램들이 서로 상호작용하는 것을 도와주는 매개체이다.

* API를 식당의 점원으로 예를 들어보면,

  API는 **손님**(프로그램)이 주문할 수 있게 **메뉴**(명령 목록)를 정리하고,  
   **주문**(명령)을 받으면 **요리사**(응용프로그램)와 상호작용하여 요청된 **메뉴**(명령에 대한 값)를 전달한다.

  `손님(프로그램) -> 점원(API) -> 요리사(응용프로그램) -> 점원(API) -> 손님(프로그램)`

* 아래는 개인 프로젝트에 급식API를 사용하여 오늘 급식을 불러오는 API를 사용해본 코드이다.

```js
const [breakfast, setBreakfast] = useState(null);
  const [lunch, setLunch] = useState(null);

  useEffect(() => {
    let now = new Date();
    let todayDate = now.getDate();

    axios
      .get(`https://school-api.xyz/api/high/F100000120?date=${todayDate}`)
      .then((result) => {
        let copyB = [...result.data.menu[0].breakfast];
        setBreakfast(copyB);
        let copyL = [...result.data.menu[0].lunch];
        setLunch(copyL);
      })
      .catch(() => {
        console.log("데이터 불러오기를 실패했습니다.");
      });
```

> [사용한 API](https://github.com/5d-jh/school-menu-api)

---

## HTTP/HTTPS?

### 개념

**HTTP**

- HTTP는 인터넷에서 데이터를 전송하기 위한 표준 프로토콜로, **웹 브라우저와 웹 서버 간의 통신에 사용된다!**

**HTTPS**

- HTTPS는 **HTTP에 데이터 암호화**가 추가된 프로토콜이다,
- **서버와 브라우저 간의 모든 통신을 암호화**하여 보안성을 강화한다.  
  이를 위해 인증서를 검증하고 암호화된 연결을 설정하며, 모든 데이터는 암호화하여 전송한다!

### 차이점

- **보안성**이다. **HTTP**는 데이터를 **암호화하지 않고 전송**하기 때문에, 중간에서 가로채어질 가능성이 있기 때문에 안전성이 보장되지 않는다.  
  반면에 **HTTPS**는 **데이터를 암호화하여 전송**하기 때문에, 데이터의 안전성이 높아지며, 중간에서 가로채어지더라도 안전하다.
