# Object

## object
### 싱글턴 클래스
- 싱글턴이란 객체의 인스턴스를 1개만 생성하여 계속 재사용 하는 패턴

- Java에서 싱글턴은 호출될 때 인스턴스가 생성됨 /
 코틀린은 프로세스가 시작될 때 인스턴스가 생성


```kt
object CarFactory {
//Class가 있어야 할 위치에 object가 들어가면 싱글턴으로 동작
    val cars = mutableListOf<Car>()

    fun makeCar(horsepowers: Int): Car {
        val car = Car(horsepowers)
        cars.add(car)
        return car
    }
}

class Car(power: Int) {
}
```
```kt
val car = CarFactory.makeCar(150)
println(CarFactory.cars.size)
// 싱글턴으로 구현이 되었기 떄문에 여러번 호출해도 CarFactory객체는 한번만 생성이 된다.
```

### 익명 클래스를 만들 때
- 클래스가 한 번만 활용되어야 하는 경우에 사용한다. 
```kt
object : [인터페이스 명] {
    [인터페이스에서 구현해야하는 fun]
}
//class와 다른 점은 클래스명 대신에 object가 들어걌다는 점

 start(object : Vehicle {
    override fun drive() = "Driving really fast"
})
```