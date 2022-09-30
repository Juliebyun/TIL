# Coroutine

```kt
fun main() = runBlocking {
    doWorld()
    println("Done")
}

suspend fun doWorld() = coroutineScope {
    launch {
        delay(2000L)
        println("World 2")
    }
    launch {
        delay(1000L)
        println("World 1")
    }
    println("Hello")
    //먼저 hello가 나오고 launch가 실행된다.
}
```

### suspend fun 
- 코루틴은 일시중단이 가능하기 때문에 코루틴 내부에서는 suspend fun 이렇게 함수를 만들어주어야한다.
- 코루틴 내에서 fun을 쓰면 오류가 난다.

### CoroutineScope
- 코루틴은 코루틴 스코프 안에서 실행된다.
```CoroutineScope.launch{
    //내용
}
```

### ViewModelScope
- 뷰모델 사용시 뷰모델 인스턴스에서 사용하기 위해 제공되는 스코프이다.

## 코루틴을 시작할 수 있는 두 가지

### launch
- 코루틴 빌더
- 결과를 반환하지 않는다. (실행하고 망각 코루틴)
```kt
with(CoroutineScope(Dispatchers.Main)){
    val job: Job = launch{ println(1) }
    //launch 수행시 job이 반환된다.
}
```

### async
- 코루틴 빌더
- launch와 달리 결과까지 반환할 수 있다.
- 코루틴을 생성하고 중단, 지연까지 할 수 있다. (suspend 함수 내에서만 사용 가능)

## 코루틴에서 사용하는 내부함수
### cancel
- 코루틴의 동작을 멈출 수 있다.
- 하나의 스코프 안에 여러 코루틴이 존재하는 경우 하위 코루틴 또한 모두 멈춘다.

### deley
- delay는 다른 코루틴에 실행을 양보한다.

### join
- 코루틴 내부에 여러 launch 블록이 있는 경우 순서를 정해야한다면 join()을 사용해서 순차적으로 실행하도록 할 수 있다.
```kt
CoroutineScope(Dispatchers.Default).launch {
    launch{
        for (i in 0..5){
            delay(500)
            Log.d("코루틴", "$i")
        }
    }.join
    //순차적으로 실행

    launch{
        for (i in 6..20){
            delay(500)
            Log.d("코루틴", "$i")
        }
    }.join
}
```