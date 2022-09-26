# Collection

## List

```kt
val fruits = listOf<String>("apple", "banana", "kiwi", "peach")
//수정 불가능한 리스트
// val fruits= listOf("apple", "banana", "kiwi", "peach") -> 타입 생략 가능
println("fruits.size: ${fruits.size}") //0부터 시작
println("fruits.get(2): ${fruits.get(2)}")
println("fruits[3]: ${fruits[3]}")
println("fruits.indexOf(\"peach\"): ${fruits.indexOf("peach")}")
//복숭아의 순서 찾기


//fruits.size: 4
//fruits.get(2): kiwi
//fruits[3]: peach
//fruits.indexOf("peach"): 3
```



```kt
val fruits= mutableListOf<String>("apple", "banana", "kiwi", "peach")
//mutableListOf : 수정 가능한 객체
fruits.remove("apple")
fruits.add("grape")
println("fruits: $fruits")

fruits.addAll(listOf("melon", "cherry"))
println("fruits: $fruits")
fruits.removeAt(3) //3번째 순서에 있는 거 삭제
println("fruits: $fruits")

//fruits: [banana, kiwi, peach, grape]
//fruits: [banana, kiwi, peach, grape, melon, cherry]
//fruits: [banana, kiwi, peach, melon, cherry]
```

## Set

```kt
val numbers = setOf<Int>(33, 22, 11, 1, 22, 3)
//수정 불가능한 객체
println(numbers)
println("numbers.size: ${numbers.size}")
println("numbers.contains(1): ${numbers.contains(1)}") //1이 포함되어있는지의 유무
println("numbers.isEmpty(): ${numbers.isEmpty()}") //문자열이 ""인지 유무

//[33, 22, 11, 1, 3]
//numbers.size: 5
//numbers.contains(1): true 
//numbers.isEmpty(): false
```

```kt
val numbers = mutableSetOf<Int>(33, 22, 11, 1, 22, 3)
println(numbers)
numbers.add(100)
numbers.remove(33)
println(numbers)
numbers.removeIf({ it < 10 }) // 10 이하의 숫자를 삭제
println(numbers)

//[33, 22, 11, 1, 3]
//[22, 11, 1, 3, 100]
//[22, 11, 100]

## Map

```kt
val numbersMap = mapOf<String, String>(
    "1" to "one", "2" to "two", "3" to "three")
println("numbersMap: $numbersMap")
val numbersMap2 = mapOf(Pair("1", "one"), Pair("2", "two"), Pair("3", "three"))
println("numbersMap2: $numbersMap2")

// numbersMap: {1=one, 2=two, 3=three}
// numbersMap2: {1=one, 2=two, 3=three}
```

```kt
val numbersMap = mutableMapOf<String, String>(
        "1" to "one", "2" to "two", "3" to "three")
        //수정 가능한 map
println("numbersMap: $numbersMap")

numbersMap.put("4", "four")
numbersMap["5"] = "five"
println("numbersMap: $numbersMap")

numbersMap.remove("1")
println("numbersMap: $numbersMap")

numbersMap.clear()
println("numbersMap: $numbersMap")

numbersMap: {1=one, 2=two, 3=three}
numbersMap: {1=one, 2=two, 3=three, 4=four, 5=five}
numbersMap: {2=two, 3=three, 4=four, 5=five}
numbersMap: {}
```

## Collection

```kt
fun printAll(strings: Collection<String>) {
    for(s in strings) print("$s ")
    println()
}

val stringList = listOf("one", "two", "one")
printAll(stringList)

val stringSet = setOf("one", "two", "three")
printAll(stringSet)

//one two one
//one two three
```