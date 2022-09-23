# 생성자 constructor

```kt
class ConstructorTest(val name: String, var age:Int){
    
}
// 클래스
```
- 클래스는 각각의 생성자를 가지고 있다.
- 생성자는 인스턴스화 될 때 호출된다. = 인스턴스화를 하는 건 생성자를 호출
    - 인스턴스화란?   
    클래스로 객체를 찍어내는 것
    ```kt
    val dialog = Dialog(this) // Dialog 클래스로 인스턴스화
    val dialog2 = Dialog(this)
    val a = A("") // A 클래스로 인스턴스화
    // 인스턴스화
    ```
```kt
(val name: String, var age:Int)
// 매개변수
```

```kt
ConstructorTest(val name: String, var age:Int)
// 생성자
```

```kt
class ConstructorTest(/*인자값*/val name: String){
    constructor(name: String, age : Int):this(/*인자값*/ name)
}
// 기본 생성자의 인자가 있는 경우
```

```kt
class ConstructorTest(val name: String, var age:Int){
    constructor():this(name,age)
    // 오류남
}
```
- 갯수는 같아도 타입이 다르면 상관 없다. 대신 둘 다 같으면 에러가 남   
```kt
class ConstructorTest(val name: String, var age:Int){
    constructor():this("",0)
} // 오류 안 남
```
- this()는 기본 생성자 외의 생성자에서 꼭 호출해야함
- constructor()을 해당 클래스가 아닌 바깥에서 부르려면 클래스 이름을 적고, 같은 클래스이면 this를 쓴다.   


# Init 함수
- 매개변수가 없고 반환되는 값이 없다
- 생성자를 통해 인스턴스가 만들어 질 때 호출되는 함수이다
```kt
class Person(var name:Any, var age: Any){
    init{
        println("${this.name} ${this.age} 기본 생성자 실행")
    }
}
// Any는 어떤 타입이든 데이터 대입이 가능하다
```

