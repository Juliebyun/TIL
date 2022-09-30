# Delegates

## Observable
- 프로퍼티의 데이터가 변할 떄마다 callback을 받을 수 있다.

```kt
var observed = false
var max: Int by Delegates.observable(0) { property, oldValue, newValue ->
    println("Changing max to $newValue")
    observed = true
}

fun main() {
    println(max) // 0
    println("observed is ${observed}") // false
    max = 10
    println(max) // 10
    println("observed is ${observed}") // true
}

//0
//observed is false
//Changing max to 10
//10
//observed is true


//max를 10으로 변경할 때 observable{} 호출됨
//-> 변한 값과 함께 observed is true가 나옴

```
