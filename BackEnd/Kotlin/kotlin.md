## Kotlin

간결한 문법과 안정성과 생산성을 보장하여 개발된 자바와 100% 호환되는 프로그래밍 언어이다.

### 특징

- **간결한 문법**
  - 세미콜론 안적어도 됨, new 키워드 없이 객체 생성 가능, 타입 추론
- **null 안정성**
  - ?, !! 을 이용하여 null 값을 구분할수 있다.  
    (런타임 에러를 줄일 수 있음)
- 정적 타입 지정 언어
- 함수형 프로그래밍

**자바와 호환도 잘 되면서 실용적으로 간결하고 안정한 언어이다. 🚀**

## 기본문법

## 변수

```kt
var 변수명: 타입 = 값
```

#### var / val

- var : 읽기 / 쓰기
- val : 읽기

```kt
fun main(args: Array<String>) {
    var i: Int = 10
    val j: Int = 10

    i = 20
    // j = 20 // Error : Val cannot be reassigned

    println(i)
    println(j)
}
```

### Int / Int? | String / String?

- 코틀린의 `Int`는 `null`을 허용하지 않기 때문에 `null`을 허용 하려면 타입에 `?` 붙여서 선언한다.

- `String`도 마찬가지로 `null`을 허용하지 않기 때문에 `null`을 허용하려면 타입에 `?` 붙여서 선언해야한다.

```kt
fun main(args: Array<String>) {
    var i: Int = 10
    var j: Int? = 10

    var k: String = "ABC"
    var l: String? = "ABC"

    // i = null // Null can not be a value of a non-null type Int
    j = null

    // k = null // Null can not be a value of a non-null type String
    l = null
}

```

### 타입추론

- 코틀린은 타입추론으로 변수에 들어오는 값을 보고 타입을 알아서 지정해줌

```kt
fun main(args: Array<String>) {
    val s = "ABC" // String
    val i = 1 // int
    val l = 1L // long
    val d = 1.0 // double
    val f = 1.0f // float

    println("s = " + s::class)
    println("i = " + i::class)
    println("l = " + l::class)
    println("d = " + d::class)
    println("f = " + f::class)
}
```

## if when

### if

```kt
fun main(args: Array<String>) {
    val priceA = 100
    val priceB = 200

    if (priceA >= priceB) {
        println("priceA = $priceA")
    } else {
        println("priceB = $priceB")
    }
}
```

### in 체크

```kt
fun main(args: Array<String>) {
    val price = 100

    if (price in arrayOf(100,200,300)) {
        println("contain")
    } else {
        println("not contain")
    }
}

```

### when

```kt
fun main(args: Array<String>) {
    val price = 100

    when (price) {
        100 -> println("1. price = $price")
        200 -> println("2. price = $price")
        300 -> println("3. price = $price")
        else -> println("4. Not")
    }
}

```

### 범위 비교

```kt
fun main(args: Array<String>) {
    val price = 100

    when (price) {
        in 100..199 -> println("1. price = $price")
        in 200..299 -> println("2. price = $price")
        in 300..399 -> println("3. price = $price")
        else -> println("4. Not")
    }

}
```
