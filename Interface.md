# Interface
- 인스턴스화가 불가능하다.
    - 인터페이스를 상속 받게 해서 같은 타입 같이 사용할 수 있게 한다   
    ex) Usecase 파일

```kt
interface OnClickListener {
        fun onClick(v : View)
    }
```

```kt
interface ExchangeRepository {
    suspend fun getExchangeInfo(): ExchangeInfoModel?
```

```kt
class InterfaceExample {
}
fun main(){
    val viewClick = ViewClick(2, 3)
    println(viewClick.changeSize())
}
interface OnClickListener{
    val clickValue : Int
    var clickValue2 : Int
    fun onClick()
    //인터페이스를 사용하는 이유
    //비슷한 기능을 갖고 있는 클래스들의
    //형태를 통일 시키기 위해서
    // 한 클래스에서 여러 interface를 상속받을 수 있다 *****
}```
```kt
interface OnChangeListener{
    fun onChange()
}
class ViewClick(override val clickValue: Int /* 필드도 오버라이드 가능 */, override var clickValue2: Int) : OnClickListener, OnChangeListener{
    fun changeSize() : Int{
        return 2
    }
    //함수는 대입 X
    override fun onClick() {
        //interface를 상속한 클래스에서 interface의 함수를 무조건 override 해야한다.
        // 1번째 인터페이스 함수
    }
    override fun onChange() {
        // 2번째 인터페이스 함수
    }
}
```


```kt
class ButtonClick : OnClickListener{
    override val clickValue : Int = 2 // 변수는 init 형태로 override 가능
    override var clickValue2: Int = 1
    //val은 init{}, 생성자에서 init 가능
    //var은 어디서든지 init, change 가능
    fun changeColor(){
        // interface
        //clickValue = 3  -> val change error
        clickValue2 = 3
    }
    //override : 부모의 필드 또는 함수를 자식 클래스
    override fun onClick() {
    }
}
```

## interface와 abstract class의 차이
 - 추상 클래스는 클래스다. 인터페이스는 아님
 - 추상 클래스는 클래스를 상속 + 확장하기 위해 사용한다.
 - 인터페이스는 객체들에 대한 동일한 사용방법과 동작을 보장하기 위해 사용한다.
 - 둘 다 인스턴스화 불가능
- abstract는 일반.추상 변수,함수를 가질 수 있다.
- interface는 추상 변수, 함수만 가질 수 있다.