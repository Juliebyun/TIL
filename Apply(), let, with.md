```kt
class ApplyLetWithExample{
    val s = ""
    var s2 : String? = null
    val g = GenericExample()
    fun onClick(){
        val b = s.let {
            //항상 실행
            //코드 마지막의 값이 이 함수의 리턴
            it == ""
        }
        s2?.let {
            //null이 아닐때만 실행
        }
        if(b){
            print(s)
        }
        g.apply {
            function()//함수
            //apply 에서는 해당 클래스의 함수인것 처럼 해당 클래스의 변수, 함수를 가져다 쓸수 있다 (private 제외)

        }
        with(g){
            interfaceExample
            //with 에서는 해당 클래스의 함수인것 처럼 해당 클래스의 변수, 함수를 가져다 쓸수 있다 (private 제외)
        }
    }
}
```


## with와 apply의 차이점
- with는 R을 반환하고 apply는 T를 반환한다.
- T는 apply 함수를 사용할 변수의 타입이다.
```kt
fun <T> T.apply{
        //선언 하는 법
    } 
    value.apply{
        //사용 하는 법 
        // T는 value의 타입이 된다. 만약에 value가 Int가 되면 Int고 String이면 String이 된다.
    }
    ```