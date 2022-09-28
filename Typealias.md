# Typealias.md
- 존재하는 타입의 새로운 이름 또는 별칭을 만들어준다.
- 타입의 이름이 너무 길 때 짧은 이름을 만드는 데 유용하다

```kt
val pathPoints = MutableLiveData<MutableList<MutableList<LatLng>>>()
//이렇게 쓰면 너무 복잡하고 어려워 보이니까

typealias Polyline = MutableList<LatLng>
typealias Polylines = MutableList<Polyline>
// 간단하게 바꿔서 사용할 수 있다.

val pathPoints = MutableLiveData<Polylines>()
