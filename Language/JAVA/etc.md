# 상수
상수는 C에서처럼 const가 아닌 final로 선언하고 반드시 선언과 동시에 초기화 해줘야한다.
```
final int AGES = 30;
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

