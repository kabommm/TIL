# 상수-final 제어자
상수는 C에서처럼 const가 아닌 final로 선언하고 반드시 선언과 동시에 초기화 해줘야한다.
```
final int AGES = 30;
```

```
final class Car {                    // 이 클래스는 상속을 통해 서브 클래스를 생성할 수 없음.

    final int VAR;                   // 이 필드는 상수화되어 값을 변경할 수 없음.

    final void brake() {             // 이 메소드는 오버라이딩을 통해 재정의할 수 없음.

        final double MAX_NUM = 10.2; // 이 지역 변수는 상수화되어 값을 변경할 수 없음.

    }

}
```

# static 제어자

'공통적인'이라는 의미로 static 제어자를 변수에 사용하면 해당 변수를 클래스 변수로 만들어 줍니다.

자바에서 static 제어자를 사용할 수 있는 대상 - 메소드, 필드, 초기화 블록

특징

1. 프로그램 시작시 최초에 단 한 번만 생성되고 초기화됩니다.

2. 인스턴스를 생성하지 않고도 바로 사용할 수 있게 됩니다.

3. 해당 클래스의 모든 인스턴스가 공유합니다.

# abstract 제어자

선언부만 있고 구현부가 없는 메소드를 추상 메소드라 하며, 반드시 abstract 제어자를 붙여야 합니다.

또한, 하나 이상의 추상 메소드가 포함하고 있는 추상 클래스도 반드시 abstract 제어자를 붙여야 합니다.

자바에서 abstract 제어자를 사용할 수 있는 대상 - 클래스, 메소드
```
abstract class Car {       // 추상 클래스

    abstract void brake(); // 추상 메소드

}
```

# 인스턴스

인스턴스 선언과 동시에 생성 : 클래스이름 객체참조변수이름 = new 클래스이름();

```
Car myCar = new Car();
```

# 생성자

인스턴스 변수를 원하는 값으로 초기화할 수 있는 메소드

```
Car(String modelName, int modelYear, String color, int maxSpeeds) {

    this.modelName = modelName;

    this.modelYear = modelYear;

    this.color = color;

    this.maxSpeed = maxSpeed;

    this.currentSpeed = 0;

}
```

자바의 모든 클래스에는 하나 이상의 생성자가 정의되어 있어야 하지만 특별히 생성자를 정의하지 않고도 인스턴스를 생성할 수 있습니다.

자바 컴파일러는 컴파일 시 클래스에 생성자가 하나도 정의되어 있지 않으면, 자동으로 다음과 같은 기본 생성자를 추가합니다.

## 참고
<http://www.tcpschool.com/java/java_modifier_ectModifier>

