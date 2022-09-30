# Equality

## ==
- 두 문자열이 같을 때 true를 리턴한다. 
```kt
fun main(args: Array<String>) {
    val a = "kotlin"
    val b = "kotlin"
    val c = "KOTLIN"
    //대소문자를 다른 문자로 인식하여 비교한다

    if (a == b)
        println("a is equal to b")

    if (a == c)
        println("a is equal to c")
}

//a is equal to b
```

## equals()
- == 랑 똑같다
```kt
fun main(args: Array<String>) {
    val a = "kotlin"
    val c = "KOTLIN"

    if (a.equals(c, false))
        println("a is equal to c (Case Sensitive)")

    if (a.equals(c, true))
        println("a is equal to c (Case Insensitive)")
}
//a is equal to b

```

## comepareTo()
- 어떤 문자열이 더 큰지에 대해 알 수 있다.
```kt
fun main(args: Array<String>) {
    val a = "kotlin"
    val b = "kotlin"
    val c = "KOTLIN"

    if (a.compareTo(b) == 0)
        println("a is equal to b")

    if (a.compareTo(c) > 0)
        println("a is greater than c")

    if (c.compareTo(a) < 0)
        println("c is less than a")
}
//a is equal to b
//a is greater than c
//c is less than a
```