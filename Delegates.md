# Delegate Pattern
- 어떤 기능을 자신이 수행하지 않고 다른 객체에 위임하여 해당 객체가 일을 수행하도록 구성한 디자인 패턴이다 

```kt
// delegage pattern을 쉽게 제공하는 게 by이다.
interface Base {
    fun print()
}

// delegate
class BaseImpl1(val x: Int) : Base {
    override fun print() { println("BaseImpl1 $x") }
}

// delegate
class BaseImpl2(val x: Int) : Base {
    override fun print() { println("BaseImpl2 $x") }
}

// delegator
class Derived(b: Base) : Base {
    var b: Base = b

    override fun print() {
        b.print()
    }
    
}

fun main() {
    val b1 = BaseImpl1(10)
    Derived(b1).print()

    val b2 = BaseImpl2(10)
    Derived(b2).print()
    //클래스화와 상속을 해서 코드 재활용성을 높일 수 있다.
}