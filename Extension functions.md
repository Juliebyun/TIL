# Extension functions (확장함수)
- 만약에 MutableList에 추가 기능을 더하고 싶으면 .함수를 하면 MutableList의 기능과 추가한 함수 기능을 다 쓸 수 있다. 

```kt
fun <T> MutableList<T>.swap(index1: Int, index2: Int) {
    val tmp = this[index1] 
    this[index1] = this[index2]
    this[index2] = tmp
}
//Mutable에는 swap 기능이 없지만 swap을 추가해서 쓸 수 있게 되었다.
```