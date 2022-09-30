# Callback
- 어떤 함수가 호출되고 순차적으로 다음 작업을 실행해야 할 때 사용한다.
- A가 이 작업을 할 동안 B가 다른 작업을 하고 난 뒤에 A에게 다 했다고 알려주는게 콜백함수이다.

```kt
fun first( second ){
    print("first on")
    second( )
}

fun second( ){
    print("second on")
}

main( ) {
    first( ) 
    //결과 : first on -> second on
}
```

```kt
class MainActivity: AppCompatActivity(){
    override fun onCreate(savedInstanceState: Bundel?){
        //생략
        callbackMethod(paramFunc = {
            Log.d("myTag", "paramFunc 호출됨")
        }) 

    }

    private fun callbackMethod( paramFunc : ()-> Unit){
        Log.d("myTag","MainActivity called this func")
        Handelr().postDelayed({
            paramFunc()
        }, 1000L)
    }
} //callbackMethod가 실행되고 1초 뒤에 paramFunc가 호출되는 코드이다.
//물론 콜백함수안에 데이터를 담을 수 있다.