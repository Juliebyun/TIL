# Generic

## Generic이란?
- 제너릭을 통해 클래스나 메서드에서 사용할 내부 데이터 타입을 미리 지정하는 방법
    ### 장점
    1. 타입 안정성 증가
    2. 객체애 대한 확장성근ㄷ

```kt
class GenericExample {
    val interfaceExample = object : GenericInterface<String>{
        override val genericInterfaceValue: String
            get() = "genericInterfaceValue"
        override fun genericInterfaceFunction() : String {
            return "genericInterfaceFunction"
        }
    }
    val intGenericExample = object : GenericInterface<Int>{
        override val genericInterfaceValue: Int
            get() = 1
        //setter : 값을 세팅
        //getter : 값을 반환? 불러오기?
        override fun genericInterfaceFunction(): Int {
            return 2
        }
    }
    val arrayList = ArrayList<Int>() //int로 선언된거다
    fun function(){
        intGenericExample.genericInterfaceValue
        arrayList.add(1) //int가 선언되어 있어서 숫자만 들어가진다.
        //String으로 바뀌면 add("string")가능.
    }
}
interface GenericInterface<T>{ // T에 Int나 String같은 타입이나 심지어 클래스 이름도 들어갈 수 있다.
    val genericInterfaceValue : T
    fun genericInterfaceFunction() : T
}
```