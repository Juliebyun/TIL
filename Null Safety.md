# Null Safety
- 코틀린은 기본적으로 null이 안 돼서 null을 쓰고 싶으면 따로 처리를 해주어야한다
```kt
var a : String = "abc"
a = null //컴파일 에러 발생

var b: String? = "abc"
b = null // ok
print(b)
```

## Safe Calls
- 안전한 호출 연산자인 ?.을 이용하는 방법
```kt
val a = "Kotlin"
val b : String? = null
println(b?.length)
println(a?.length) //Unnecessary safe call
```

## 엘비스 연산자
```kt
val l = ?.length ?: -1
//?: 연산자는 결과값이 null이 아니면 연산자 왼쪽의 값을 반환하고, 값이 null이면 오른쪽의 값을 반환한다.
```

## filterNotNull
- null을 입력할 수 있는 요소 컬렉션이 있을 때, null아 아닌 요소를 필터링 하고 싶다면 filterNotNull 사용
```kt
val nullableList: List<Int?> = listOf(1, 2, null, 4)
val intList: List<Int> = nullableList.filterNotNull()
```