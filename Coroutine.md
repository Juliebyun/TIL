# Coroutine
- 비선점형 멀티태스킹, 비동기 프로그래밍이다.
    - 비선점형 : 강제로 cpu 사용권을 뺏을 수 없다. (Coroutine)
    - 선점형 : cpu를 사용하고 있더라도 뺏어서 중단 시키기 가능 (Thread)
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
### runBlocking
- 주어진 블록이 완료될 떄까지 현재 스레드를 멈추는 새 코루틴을 생성해 실행하는 코루틴 빌더이다.
- onCreate에서 delay를 쓸 수 없다. -> 그래서 delay를 해주고 싶을 때 runBlocking 안에 delay를 넣으면 된다.

### suspend fun 
- 코루틴은 일시중단이 가능하기 때문에 코루틴 내부에서는 suspend fun 이렇게 함수를 만들어주어야한다.
- 코루틴 내에서 그냥 fun을 쓰면 오류가 난다.
- 코루틴 내 or 다른 suspend 함수에서만 호출할 수 있다.

### CoroutineScope
- 코루틴은 코루틴 스코프 안에서 실행된다.
```
CoroutineScope.launch{
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
    // 메인 스레드다. UI 갱신이나 view 작업에 사용된다.
    val job: Job = launch{ println(1) }
    //launch 수행시 job이 반환된다.
}
CoroutineScope(IO).launch{
    //네트워킹이나 내부 DB등 백그라운드에 필요한 작업을 수행할 때 사용한다.
}
CoroutineScope(Default).launch{
    // 크기가 큰 리스크를 다루거나 무거운 연산을 할 때 사용한다.
}
```

### async
- 코루틴 빌더
- launch와 달리 결과까지 반환할 수 있다.
- 코루틴을 생성하고 중단, 지연까지 할 수 있다. (suspend 함수 내에서만 사용 가능)

## Coroutine Context
- 코루틴을 처리하는 방법들
### Dispachers
- .Default (CPU를 많이 사용하는 무거운 작업에 사용)
- .IO (Network등에 사용)
- .Main (suspend 함수 호출, LiveData 업데이트, 메인 스레드에서 동작)
- .Unconfined (첫번째 지연점까지만 실행된다. 메인스레드에서 동작한다.)

### Job
- 스코프와 코루틴의 생명주기를 지정할 수 있다.

## 코루틴에서 사용하는 내부함수
### cancel
- 코루틴의 동작을 멈출 수 있다.
- 하나의 스코프 안에 여러 코루틴이 존재하는 경우 하위 코루틴 또한 모두 멈춘다.

### deley
- delay는 한 스레드 안에 있는 여러 코루틴 중에 코루틴 하나만 멈춘다.
- Thread.sleep은 스레드 하나를 멈춘다 = 그 안에 있는 코루틴이 모두 멈춘다.

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