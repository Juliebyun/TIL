#  Thread

## 메인 스레드
- 화면의 UI를 그리는 처리를 담당한다.
- 작업에 일정시간 응답이 없으면 ANR 팝업을 띄운다

## 백그라운드 스레드
- 네트위크 작업 및 파일 다운로드 등 시간이 오래 걸리는 작업들이다

```kt
class ThreadTest : Thread(){
    override fun run(){
        var i = 0
        while(i < 10) {
            i += 1
            Log.i(ThreadTest, "i = ${i}")
        }
    }// i가 10번 찍힌다
} //기본적인 스레드 생성법
```
### Runnable Thread
- Thread()를 상속받으면 다른 클래스를 상속 받을 수 없다.
하지만 Runnable을 상속받은 스레드는 다른 클래스도 구현할 수 있도록 지원한다.
```kt
class RunnableTest : Runnable {
    override fun run(){
        var i = 0
        while( i < 10) {
            i += 1
            Log.i("RunnableTest", "i = ${i}")
        }
    }
} //Runnable Thread
```

### Kotlin의 Thread()
```kt
class MainActivity : AppCompatActivity(){
    override fun onCreate(savedInstanceState : Bundle?){
        thread(start = true){
            //thread() 안에 파라미터를 start = true로 전달하면 블럭 안의 코드를 실행할 수 있습니다.
            var i = 0
            while(i<10){
                i+=1
                Log.d("Main", "i = ${i})
            }
        }
    }
}//스레드에서는 UI에 접근 할 수 없다.
```

```kt
thread(start = true){
           
            var i = 0
            while(i<10){
                i+=1
                runOnUiThread { //runOnUiThread를 사용하면 UI에 접근 할 수 있다.
                    textview.text = "카운트 : ${i}"
                }
                Thread.sleep(1000)
            }
