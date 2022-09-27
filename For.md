# For문

```kt
for (i in 1..3) {
    println(i)
}
for (i in 6 downTo 0 step 2) {
    println(i)
}
//1236420
```

```kt
val array = arrayOf("a", "b", "c")
    for (i in array.indices) {
        println(array[i])
    }

    //a b c
```

## Foreach문

```kt
val numList = arrayListOf(1,2,3,4,5,6)

numList.forEach{
  i -> println("${i}")  
}

numList.forEach{
    println(it)
}
```
