# 싱글톤패턴

싱글톤 패턴이란 특정 객체의 인스턴스가 하나만 생성되게 하는 패턴이다.

한 번의 new 연산자만을 사용하여 메모리가 고정되어있어 효율적이고, 객체에 접근시 이미 생성되어있는 하나의 메모리만을 찾아가기때문에 속도측면에서도 이득이 된다.

```java
public class SingleTonClass {
    private static final SingleTonClass singleTonClass = new SingleTonClass();//초기화를 이용함
    private SingleTonClass() { // 외부생성막음

    }

    public static SingleTonClass get() {
        return singleTonClass; //이미 생성된거만 가져옴
    }

    public void method() {

    }
}
```

이런식으로 상수필드에서 초기화를 이용해 객체를 생성해준다. 이후 메소드를 통해서 그 객체를 가져오게하면

하나의 인스턴스만 사용할 수 있게된다.

하지만 내부에서 생성자를 사용하여 DIP원칙을 위반하고 테스트가 어려운 점 등 찾아보니 단점도 꽤 많으니 주의해서 사용하자