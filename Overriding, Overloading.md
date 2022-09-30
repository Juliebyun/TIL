# Overriding
- 오버 라이딩은 부모 클래스의 함수를 자식 클래스에서 재정의 하는것
- 부모 클래스와 overriding 하려는 함수 둘 다 open을 붙여야한다.
- 같은 이름과 형태의 함수를 새롭게 재정의 하는 것
```kt
fun main() {
    var sup = Beverage()
    var sub1 = Cola()
    var sub2 = Coffee()
    println("money : ${sup.drink(2000)}")
    println("money : ${sub1.drink(2000)}")
    println("money : ${sub2.drink(2000)}")
}

open class Beverage(){
   open fun drink(money: Int): Int{
       println("슈퍼클래스의 drink함수")
       return money
   }
}

class Cola() : Beverage(){
    var price = 1500
    override fun drink(money: Int): Int{
        println("콜라를 마십니다.")
        return money - this.price
    }
}

class Coffee() : Beverage(){
    var price = 1000
    override fun drink(money: Int): Int{
        println("커피를 마십니다.")
        return money - this.price
    }
    //Beverage라는 클래스를 Cola와 Coffee클래스가 상속받아 drink라는 함수를 서로 다르게 overriding한 것을 볼 수 있다
}
```
  
## Overloading
- 이름은 같지만 형태를 다르게 하여 (다른 타입을 반환하거나 매개변수)함수를 여러 개 선언하는 것
- fun1이라는 함수명을 생각해볼 때, 이름은 같지만 매개변수를 다르게 해서 fun1이라는 함수를 2개, 3개도 만들 수 있는 것

```kt
fun main() {
    fun add(a: Int, b: Int) = a+b
    fun add(a: Int, b: Int, c: Int) = a+b+c
    fun add(a: Int, b: Char){
        println("${a}와 ${b} 1번")
    }
    fun add(a: Char, b: Int){
        println("${a}와 ${b} 2번")
    }
    
    println(add(1, 2))
    println(add(3, 4, 5))
    add(1, 'a')
    add('a', 1)
    //함수 이름은 다 같지만 결과는 다 다르게 나온다
}
```
