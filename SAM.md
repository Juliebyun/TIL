# SAM
- Single Abstract Method의 약자이다
- 함수형 인터페이스이다.
- 콜백 또는 큰 틀(인터페이스)을 만들어 준다는 느낌으로 사용할 수 있다. 

SAM 생성자를 이용해 인스턴스를 생성한 예제
```kt
val onClickListInstance = View.OnClickListener { println("onClick") }
//this로 인스턴스 자신을 참조할 수 없다
```

```kt
public interface  TestInterface{
    void function_01();
}
val testInstance = TestInterface { println("Test") }
//SAM 인터페이스에만 SAM 생성자를 지원한다. 
```


