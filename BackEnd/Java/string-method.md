## 문자열 메소드

> 문자열은 불변하다. 문자열을 스스로 변경하는 메소드는 없음

- 문자열 길이 반환

```java
int int3 = "Hello".length();
```

- 빈 문자열 여부

```java
String s1 = "";
String s2 = " \t\n";

//  💡isEmpty : 문자열의 길이가 0인지 여부
boolean b1 = s1.isEmpty();
boolean b2 = s2.isEmpty();

//  💡isBlank : 공백(white space)을 제외한 문자열의 길이가 0인지 여부
boolean b3 = s1.isBlank();
boolean b4 = s2.isBlank();
```

- 앞뒤의 공백 제거

```java
String str3 = "\t h e l l o \n";

//  💡 trim : 앞뒤의 공백(white space) 제거
String str4 = str3.trim(); // "h e l l o"
```

- 문자 반환

```java
String s1 = "Hello";

// chatAt() ~번째 문자 반환
char c1 = s1.charAt(0);
```

- 문자(열)의 위치 반환

```java
String str2 = "Aa Ab Aa DEF";

//  💡 indexOf/lastIndexOf : 일치하는 첫/마지막 문자열의 위치
//  앞에서부터 카운트해서 int로 반환


//  두 번째 인자 : ~번째 이후/이전부터 셈
int int1 = str2.indexOf('A'); // 0
int int2 = str2.indexOf('A', 2); // 3

int int3 = str2.lastIndexOf("Aa"); // 6
```

- 포함 여부 확인

```java
String str_b1 = "옛날에 호랑이가 한 마리 살았어요.";

//  💡 contains : 포함 여부
boolean bool_b1 = str_b1.contains("호랑이");

//  💡 startsWith : (주어진 위치에서) 해당 문자열로 시작 여부
boolean bool_b3 = str_b1.startsWith("옛날에"); // true
boolean bool_b4 = str_b1.startsWith("호랑이"); // false
boolean bool_b5 = str_b1.startsWith("호랑이", 4); // true

//  💡 endsWith : 해당 문자열로 끝남 여부
boolean bool_b6 = str_b1.endsWith("살았어요."); // true
boolean bool_b7 = str_b1.endsWith("호랑이"); // false
```

- 정규표현식
  > .matches()

```java
String emailRegex = "^[\\w-\\.]+@([\\w-]+\\.)+[\\w-]{2,4}$";

String str_c1 = "vvwv309@gmail.com";
String str_c2 = "vvwv309.vvwv309.kr";
String str_c3 = "vvwv309@vvwv309@kr";

boolean bool_c1 = str_c1.matches(emailRegex);
boolean bool_c2 = str_c2.matches(emailRegex);
boolean bool_c3 = str_c3.matches(emailRegex);
```

- 문자열 비교

```java
String str_a1 = "ABC";
String str_a2 = "ABCDE";
String str_a3 = "ABCDEFG";


//  💡 compareTo : 사전순 비교에 따라 양수 또는 음수 반환

//  같은 문자열이면 0 반환
int int_a1 = str_a1.compareTo(str_a1);

//  시작하는 부분이 같을 때는 글자 길이의 차이 반환
int int_a2 = str_a2.compareTo(str_a1); // 2

// "ABCDE".compareTo("ABC");
// 5, 3 -> 2

int int_a3 = str_a1.compareTo(str_a3); // -4
int int_a4 = str_a2.compareTo(str_a3); // -2
int int_a5 = str_a3.compareTo(str_a1); // 4


String str_a4 = "HIJKLMN";

//  시작하는 부분이 다를 때는 첫 글자의 정수값 차이 반환

// A
// H

// 두 글자의 정수값 차

int int_a6 = str_a1.compareTo(str_a4); // -7
int int_a7 = str_a4.compareTo(str_a3); //7
```

- 대소문자 변환

```java
String s1 = "Hello, World!";

// 💡 toUpperCase / toLowerCase : 모두 대문자/소문자로 변환
String up1 = s1.toUpperCase();
String dn1 = s1.toLowerCase();
```
