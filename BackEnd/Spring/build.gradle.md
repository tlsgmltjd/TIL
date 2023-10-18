### build.gradle

- 빌드 스크립트라고도 불리며 gradle을 이용해 프로젝트를 빌드하고 의존성을 관리하기 위해 작성됨
- groovy 언어을 사용해 작성되었고, kotiln으로도 작성할 수 있음

### plugins 블록

```groovy
plugins {
	id 'java'
	id 'org.springframework.boot' version '3.1.3'
	id 'io.spring.dependency-management' version '1.1.3'
}
```

- `id 'org.springframework.boot' version '3.1.3'`
- 이름 : org.springframework.boot \ 버전 3.1.3
- 스프링을 빌드했을 때 실행가능한 jar 파일이 나오게 도와줌
- 스프링 애플리케이션을 실행할 수 있게 도와주고 또 다른 플러그인들이 잘 적용될 수 있게 해준다.

* `id 'io.spring.dependency-management' version '1.1.3'`
* 외부 라이브버리, 프레임워크의 버전관리에 도움을 주고 서로 얽혀있는 의존성을 처리하는데 도와줌

- `id 'java'`
- 자바 프로젝트로 개발하는데 필요한 기능을 추가해주고 다른 JVM 언어 gradle 플로그인을 사용할 수 있는 기반을 마련한다.

### 프로젝트 관련된 설정

```groovy
group = 'oneus'
version = '0.0.1-SNAPSHOT'

java {
	sourceCompatibility = '17'
}
```

- 프로젝트의 그룹, 빌드 결과물에 프로젝트 그룹에 대한 정보가 들어있다.
- 프로젝트의 버전
- 프로젝트가 사용하고 있는 JDK 버전

### repositories 블록

```groovy
repositories {
	mavenCentral()
}
```

- mavenCentral() : 프레임워크를 메이븐 중앙저장소에서 가져오렴

### dependencies 블록

```groovy
dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
	implementation 'org.springframework.boot:spring-boot-starter-security'
	implementation 'org.springframework.boot:spring-boot-starter-web'
	implementation 'org.springframework.boot:spring-boot-starter-websocket'
	compileOnly 'org.projectlombok:lombok'
	runtimeOnly 'com.mysql:mysql-connector-j'
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
	testImplementation 'org.springframework.security:spring-security-test'
	runtimeOnly 'com.h2database:h2'
	implementation 'org.springframework.boot:spring-boot-starter-validation'
}
```

- implementation : 해당 의존성을 항시 사용한다
- runtimeOnly : 코드를 실행할 때만 해당 의존성을 사용한다.
- testImplementation : 테스트 코드를 컴파일 하거나 실행시킬 때 항시 사용한다.
- 의존성 이름을 명시해주는 부분 앞에 오는 것을 **Dependency Configuration**

- `org.springframework.boot:spring-boot-starter-data-jpa`
  - JPA를 스프링과 함께 사용하기 위해 필요한 모든 것
- `org.springframework.boot:spring-boot-starter-web`
  - 스프링으로 web 관련 개발을 하기 위해 필요한 모든것 (톰켓, 다양한 어노테이션)
- `testImplementation 'org.springframework.boot:spring-boot-starter-test'`
  - 스프링을 사용해 테스트 코드를 작성하기 위해 필요한 라이브러리, 프레임워크가 모여있는 의존성

### 테스트를 수행할 때 Junit5를 사용하겠다

```groovy
tasks.named('test') {
	useJUnitPlatform()
}
```
