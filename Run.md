# Run

```kt
class RunExample{
    val g = GenericExample()
    fun sRun(){
        val b = g.run {
            //let과 유사하지만 this가 해당 변수의 클래스인 점이 다르다.
            interfaceExample // 해당 변수의 클래스
        }
        if(b){
            print(b) //interfaceExample
        }
    }
}
```