# lateinit, lazy
- 프로퍼티를 선언하면 기본적으로 모두 초기화해야한다.
- 하지만 초기화를 미룰 수 있는 방법 : lateinit, lazy

## lateinit 
- var로 선언된 프로퍼티만 사용 가능
- 프로퍼티에 대한 게터와 세터를 사용 불가능

```kt
class Person {
    lateinit var name: String
    //객체 지연 초기화를 시키고 싶으면 var 앞에 lateinit을 붙인다
//실행할 때까지 값이 비어있는 상태면 오류 유발 가능
    fun test() {
        if (!::name.isInitialized) { // 프로퍼티 초기화 여부 판단(코틀린 표준함수 )
            println("not initialized")
        } else {
            println("initialized")
        }
    }
}

fun main() {
    val person = Person()
    person.test()
    person.name = "backtony" // 프로퍼티 초기화(지연 초기화)
    person.test()
}
```

```kt
data class Person(var name:String, var age:Int)

lateinit var person: Person // 객체 생성 지연 초기화 -> lateinit이 없다면 컴파일 에러 발생d

fun main() {
    person = Person("backtony",27) // 생성자 호출 시점에 초기화
}
```


## lazy
- val에 지연 초기화를 하기 위해 사용한다

```kt
class LazyTest {
    init {
        println("init block") // 2
    }

    val subject by lazy { // 6
        println("lazy subject")
        "kotlin" // lazy에 의한 반환값
    }

    fun flow() {
        println("not initialized") // 4
        println("sub one : $subject") // 5 최초 접근 시점에 lazy 블록 먼저 호출 후 현재 println 출력
        //해당 프로퍼티에 접근하는 로직이 있어야 lazy를 실행한다
        println("sub two : $subject") // 7
    }
}

fun main() {
    val test = LazyTest() // 1 (코드 실행되는 순서)
    test.flow() // 3
}
```