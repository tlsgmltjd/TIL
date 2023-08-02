## Kotlin

### 변수의 형태

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
