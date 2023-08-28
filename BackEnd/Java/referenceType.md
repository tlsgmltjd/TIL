## Reference Type 자료형

### 정수 자료형

- `byte` | 1바이트
- `short` | 2바이트
- `int` | 4바이트
- `long` | 8바이트

```java
//  ⚠️ 자료형의 범주 외의 수를 담을 수 없음
byte overByte1 = 127;

//  명시적(강제) 형변환
byteNum = (byte) smallIntNum;
```

- int를 널리 사용하는 이유
  - 자바 및 다른 언어들에서 기본 자료형으로 사용
  - 다른 언어들과의 호환
  - 연산 속도가 다른 자료형보다 빠름

### 실수 자료형

- `float` | 4바이트
- `double` | 8바이트

> double은 float보다 범위도 넓고 보다 정밀한 소수 표현이 가능하다.

```java
//  float은 뒤에 f 또는 F를 붙여 표현
float float1 = 3.14f;
double double1 = 3.14;

//  ⚠️ float에는 double을 담을 수 없음
float float2 = double1;
//  반대는 가능
double double2 = float1;

float f1 = 1.1f;
float f2 = 2.2f;
double d1 = 3.3;

// float끼리의 연산은 float 반환
float f3 = f1 + f2;

//  float과 double의 연산은 double 반환
float f4 = f1 + d1; // ERROR
double f4 = f1 + d1;
```

### 문자 자료형

- `char` | 2바이트

```java
//  각 문자는 상응하는 정수를 가짐
char ch1 = 'A';
int ch1Int = (int) ch1; // 65

// 문자 리터럴과 숫자, 유니코드로 표현 가능
char cc1 = 'A';
char cc2 = 65;
char cc3 = '\u0041';
```

### 불리언 자료형

- `boolean` | 1바이트

```java
boolean bool1 = true;
boolean bool2 = false;
```
