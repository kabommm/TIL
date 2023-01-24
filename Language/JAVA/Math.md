# Math 클래스

Math 클래스의 모든 메소드는 클래스 메소드(static method)이므로, 객체를 생성하지 않고도 바로 사용할 수 있습니다.

Math 클래스는 java.lang 패키지에 포함

## 메소드

- random() 메소드
- 
random() 메소드는 0.0 이상 1.0 미만의 범위에서 임의의 double형 값을 하나 생성하여 반환합니다.

```
System.out.println((int)(Math.random() * 100)); // 0 ~ 99
```

- abs() 메소드

abs() 메소드는 전달된 값이 음수이면 그 값의 절댓값을 반환하며, 전달된 값이 양수이면 전달된 값을 그대로 반환합니다.

```
System.out.println(Math.abs(10));    // 10
System.out.println(Math.abs(-10));   // 10
```

- floor() 메소드, ceil() 메소드와 round() 메소드

floor() 메소드는 인수로 전달받은 값과 같거나 작은 수 중에서 가장 큰 정수를 반환합니다. -------- 내림

또한, ceil() 메소드는 반대로 인수로 전달받은 값과 같거나 큰 수 중에서 가장 작은 정수를 반환합니다.  ---------- 올림

round() 메소드는 전달받은 실수를 소수점 첫째 자리에서 반올림한 정수를 반환합니다. ------- 반올림

```
System.out.println(Math.floor(10.9));     // 10.0
System.out.println(Math.ceil(10.000001)); // 11.0
System.out.println(Math.round(10.4));     // 10
System.out.println(Math.round(10.5));     // 11
```

- max() 메소드와 min() 메소드

max() 메소드는 전달된 두 값을 비교하여 그중에서 큰 값을 반환하며, min() 메소드는 그중에서 작은 값을 반환합니다.

```
System.out.println(Math.max(3.14, 3.14159)); // 3.14159
System.out.println(Math.min(3.14, 3.14159)); // 3.14
```

- pow() 메소드와 sqrt() 메소드

pow() 메소드는 전달된 두 개의 double형 값을 가지고 제곱 연산을 수행합니다.

예를 들어, pow(a, b)는 a의 b 승, 즉 ab를 반환하게 됩니다.

반대로 sqrt() 메소드는 전달된 double형 값의 제곱근 값을 반환합니다.

```
System.out.println((int)Math.pow(5, 2)); // 25
System.out.println((int)Math.sqrt(25));  // 5
```

- sin() 메소드, cos() 메소드와 tan() 메소드

sin() 메소드는 전달된 double형 값의 사인값을, cos() 메소드는 코사인값을, tan() 메소드는 탄제트값을 반환합니다.

- toRaidans() 메소드

육십분법의 각도 값을 대략적인 호도법의 라디안 값으로 변환함.

```
System.out.println(Math.sin(Math.toRadians(30)));
System.out.println(Math.tan(Math.toRadians(45)));
System.out.println(Math.cos(Math.toRadians(60)));
```
