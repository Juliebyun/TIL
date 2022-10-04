# Annotation

## @Override
- 선언된 메소드가 오버라이드 되었다는 걸 나타낸다.

### @Target
- 어노테이션을 달 수 있는 구성 요소 선정

### @Retention 
- 어노테이션이 남아있는 단계를 선정합니다.
- 소스, 컴파일 타임, 런타임 중 선택 가능
런타임으로 선언하면 런타임중에 어노테이션 정보가 남아있다. 그렇지 않으면 어노테이션 정보는 지워진다.
```kt
@Retention(AnnotationRetention.RUNTIME)
```

### @Repeatable
- 이 어노테이션을 한 곳에 반복 사용 가능하게 설정
### @MustBeDocumented
- 어노테이션을 API에 포함해야 하는지, API 문서에 포함해야 하는지 설정


