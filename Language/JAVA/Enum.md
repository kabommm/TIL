# Enum 클래스

Enum 클래스는 java.lang 패키지에 포함

- 열거체의 정의 및 사용

자바에서는 enum 키워드를 사용하여 열거체를 정의할 수 있습니다.
```
enum Rainbow { RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET } //정의
Rainbow.RED //사용
```

## 메소드

- values() 메소드
values() 메소드는 해당 열거체의 모든 상수를 저장한 배열을 생성하여 반환합니다.

```
enum Rainbow { RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET }

public class Enum01 {

    public static void main(String[] args) {
        Rainbow[] arr = Rainbow.values();

        for (Rainbow rb : arr) {
            System.out.println(rb);
        }
    }
}
```

- valueOf() 메소드

valueOf() 메소드는 전달된 문자열과 일치하는 해당 열거체의 상수를 반환합니다.

```
enum Rainbow { RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET }

public class Enum02 {

    public static void main(String[] args) {
        Rainbow rb = Rainbow.valueOf("GREEN");

        System.out.println(rb);
    }
}
```

- ordinal() 메소드

ordinal() 메소드는 해당 열거체 상수가 열거체 정의에서 정의된 순서(0부터 시작)를 반환합니다.

이때 반환되는 값은 열거체 정의에서 해당 열거체 상수가 정의된 순서이며, 상숫값 자체가 아님을 명심해야 합니다.

```
enum Rainbow { RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET }

public class Enum03 {

    public static void main(String[] args) {
        int idx = Rainbow.YELLOW.ordinal();

        System.out.println(idx);
    }
}
```
## 참고
<http://www.tcpschool.com/java/java_api_enum>
