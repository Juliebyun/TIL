# Replace()
```kt
fun main(args : Array<String>) {

    /*
    [설 명]
    1. replace 는 코틀린에서 문자열을 변경할때 사용합니다
    2. replace(" ","") 는 공백을 제거할때 사용합니다
    3. replace("world","kotlin") 는 특정 문자를 변경할때 사용합니다
    */

    println("[replace 사용해 공백 제거 및 특정 문자열 변환 실시]")

    //초기 string 변수 선언 실시
    var str_data = "hello world program"
    println("초기 문자열 : "+str_data)

    //공백 제거 실시
    str_data = str_data.replace(" ","")
    println("공백 제거 : "+str_data)

    //특정 문자열 변경 실시
    str_data = str_data.replace("world","kotlin")
    println("문자 변경 : "+str_data)
    //world -> kotlin

}

//초기 문자열 : hello world program
//공백 제거 : helloworldprogram
//문자 변경 : hellokotlinprogram
```