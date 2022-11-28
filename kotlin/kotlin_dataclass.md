# Kotlin Data Class

코틀린의 DataClass는 일반 Class와 달리 다양한 메소드를 자동으로 생성해주는 클래스이다.

생성되는 메소드들은 개발하면서 자주 사용하는것들이기 때문에 일일이 롬복어노테이션을 달아서 생성해주었던 번거로움 자체가 없어진다.

DataClass가 생성해주는 대표적인 메소드들을 알아보자

- hashCode()
- copy()
- equals()
- toString()
- componentN()

이 중 copy와 componantsN메소드들에 대해 알아보겠다.

### copy()

특정 필드만 바꿔서 복사하는 메소드이다.

말그대로 복제하는것이기 때문에 원본 클래스는 바뀌지 않는다.

```kotlin
val instance = Good("name", "password")
val copyInstance = instance.copy(name = "changedName")

println(instance.name + " " + copyInstance.name)

//output
name changedname //원본 객체는 바뀌지 않음
```

### componentN()

객체를 생성하고 각 필드를 변수에 대입하기 위해선

```kotlin
val instance = Good("name", "password")

val name:String = instance.name
val password:String = instance.password
```

이런식으로 변수를 일일히 만들어야 하지만이 dataclass는 각 필드에 component1(), component2()..식으로 메소드가 생성되기때문에 

```kotlin
val instance = Good("name", "password")

val (name, password) = instance;
```

이런식으로 구조분해를 하여 변수를 할당할 수 있다.