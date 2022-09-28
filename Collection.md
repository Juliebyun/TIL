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

//add(element) : 맨 뒤에 요소 추가
//add(index, element) : 특정 인덱스 위치에 요소 추가
//addAll(index, elements) : 특정 인덱스에 컬렉션 추가. 
//removeAt(index) : 특정 인덱스에 있는 값 삭제
//remove(element) : 특정 요소 삭제
//list[index] = value : 값 수정

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

//size : 컬렉션의 크기 반환
//contains(element) : 특정 요소가 Set에 있는지 확인
//isEmpty() : 아무 값도 포함하고 있지 않을 때 true 반환
//numbers == numbersBackwards : 크기가 같고 같은 요소를 가지고 있으면 true 반환
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

//add(element) : 요소 추가
//remove(element) : 특정 요소 삭제
//removeIf(filter) : 람다 표현식으로 조건 전달. 조건에 맞는 요소 삭제.


```

## Map

```kt
val numbersMap = mapOf<String, String>(
    "1" to "one", "2" to "two", "3" to "three")
println("numbersMap: $numbersMap")
val numbersMap2 = mapOf(Pair("1", "one"), Pair("2", "two"), Pair("3", "three"))
println("numbersMap2: $numbersMap2")

// numbersMap: {1=one, 2=two, 3=three}
// numbersMap2: {1=one, 2=two, 3=three}

//map.entries : Map의 key와 value 쌍을 모두 출력
//map.keys : Map의 key 모두 출력
//map.values : Map의 value 모두 출력
//containsValue(value) : 특정 value를 가지고 있는 key 반환

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

//put(key, value) : 객체 추가
//map[key] = value : 배열 방식으로 객체 추가
//remove(key) : 특정 key값인 쌍을 삭제하고 value값 반환
//remove(key, value) : key와 value가 일치하는 원소가 있다면 삭제한 후 true 반환
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


## Set, List, Map, Collection의 차이
1. Set은 List와 달리 중복을 허용하지 않는다.
2. Map은 key, value가 쌍으로 지정되어 저장하는 Collection이다. (key는 중복이 불가 value는 중복이 가능)
