# Lamda

- 익명함수의 하나의 형태이다.
- 고차 함수에서 인자로 넘기거나 결과값으로 반환 등을 할 수 있다.
    ### 고차함수
    - 다른 함수를 인자로 받거나 함수를 반환하는 함수. 
    ```kt
    list.filter { x > 0 }
    //인자로 받으므로 고차함수
    ```
```kt
{ 변수1 : 타입, 변수2 : 타입 -> 변수1 + 변수 2 }
```

## 익명함수란?
- 일급객체다.
    ### 일급객체?
    - 다른 객체들에 적용 가능한 연산을 모두 지원하는 개체를 가르킨다.
    - 함수를 값으로 사용 , 변수에 대입하기 같은 연산이 가능하다.


람다의 장점
1. 불필요한 반복문 삭제
2. 멀티쓰레드를 활용해 병렬처리 가능

## 람다의 표현식
1. 매개변수 화살표로 이용하여 사용할 수 있다.
2. 단일 실행문이면 괄호 생략 가능
3. 함수 몸체가 return문이면 괄호 생략 불가능 (ex. x -> { return x+1; }
)

```kt
val multi = {x:Int, y:Int -> x * y}
println(multi(10,20)
val multi2: (Int, Int) -> Int = {x:Int, y: Int ->
    println("x*y)
    x*y //마지막 표현식이 반환됨
}
```

## 람다식에서 return 사용하기
```kt
fun main(){
    retFunc()
}

inline fun inlineLambda(a:Int,b:Int,out:(Int,Int)->Unit){
    out(a,b)
}
fun retFunc(){
    println("start of retFunc")//1
    inlineLambda(13,3){ a+b -> //2
        val result = a+b 
    if(result>10)return //3 10보다 크면 이 함수를 빠져나감
    println("result:"$result) //4 10보다 크면 이 문장에 도달 불가
    }
    println("end of retFunc") // 5
}
