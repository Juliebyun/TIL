# Property

- property에 값을 할당할 때는 setter, 불러올 때는 getter 호출

```kt
var stringRepresentation: String
    get() = this.toString()
    set(value) {
        setDataFromString(Vaule) // String을 parse하여 다른 프로퍼티에 값을 할당함.
    }
```

```kt

    var allByDefault: Int? // 값이 여러번 들어갈 수 있기 때문에 초기화를 시켜야한다.
var initialized = 1 // 초기화를 시키면 오류가 안 난다

val simple: Int? // 
val inferredType = 1 // Int 타입이며 디폴트 getter를 가짐.
```


```kt
var stringRepresentation: String
    get() = this.toString()
    set(value) {
        setDataFromString(Vaule) // String을 parse하여 다른 프로퍼티에 값을 할당함.
    }
    //var은 여러번 값이 들어갈 수 있기 때문에 get/set 둘 다 사용 가능하다. 그래서 var을 보통 많이 쓴다


val isEmpty: Boolean
get() = this.size == 0
//근데 val은 한번만 초기화 할 수 있기 때문에  get만 쓸 수 있다.
```

```kt
var counter = 0 
    set(value) {
        if(value >= 0) field = value
        //이렇게 if도 set안에서 쓸 수 있다.
    }
```