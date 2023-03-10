# StringBuffer 클래스

String 클래스의 인스턴스는 한 번 생성되면 그 값을 읽기만 할 수 있고, 변경할 수는 없습니다.

하지만 StringBuffer 클래스의 인스턴스는 그 값을 변경할 수도 있고, 추가할 수도 있습니다.
이를 위해 StringBuffer 클래스는 내부적으로 버퍼(buffer)라고 하는 독립적인 공간을 가집니다.

버퍼 크기의 기본값은 16개의 문자를 저장할 수 있는 크기이며, 생성자를 통해 그 크기를 별도로 설정할 수도 있습니다.

하지만 인스턴스 생성 시 사용자가 설정한 크기보다 언제나 16개의 문자를 더 저장할 수 있도록 여유 있는 크기로 생성됩니다.

덧셈(+) 연산자를 이용해 String 인스턴스의 문자열을 결합하면, 내용이 합쳐진 새로운 String 인스턴스를 생성합니다.

따라서 문자열을 많이 결합하면 결합할수록 공간의 낭비뿐만 아니라 속도 또한 매우 느려지게 됩니다.

하지만 StringBuffer 인스턴스를 사용하면 문자열을 바로 추가할 수 있으므로, 공간의 낭비도 없으며 속도도 매우 빨라집니다.

이러한 StringBuffer 클래스는 java.lang 패키지에 포함되어 제공됩니다.

- 불변 클래스(immutable class)와 가변 클래스(mutable class)

String 클래스와 같이 인스턴스가 한 번 생성되면 그 값을 변경할 수 없는 클래스를 불변 클래스(immutable class)라고 합니다.

반대로 StringBuffer 클래스와 같이 자유롭게 인스턴스의 값을 변경할 수 있는 클래스를 가변 클래스(mutable class)라고 합니다.

String 클래스와 같은 불변 클래스는 StringBuffer 클래스의 append()나 insert() 메소드와 같이 값을 변경하는 set 메소드를 포함하지 않습니다.

이렇게 불편하기만 할 것 같은 불변 클래스를 사용하는 이유는 멀티 스레드 환경에서 객체가 변화되는 상황이라면 불변 인스턴스를 사용하는 것이 좀 더 신뢰할 수 있는 코드를 작성할 수 있기 때문입니다.

즉, 하나의 객체에 접근하면서 각각의 객체가 서로 영향을 주어서는 안 되는 경우에 불변 인스턴스를 사용하면 값이 변하지 않는다는 점이 보장됩니다.

## StringBuilder vs StringBuffer

멀티쓰레드 환경 외에는 StringBuilder 성능이 좋으므로 StringBuilder사용



## 메소드

- append(값) 메소드

append() 메소드는 인수로 전달된 값을 문자열로 변환한 후, 해당 문자열의 마지막에 추가합니다.

이 메소드는 String 클래스의 concat() 메소드와 같은 결과를 반환하지만, 내부적인 처리 속도가 훨씬 빠릅니다.

```
StringBuffer str = new StringBuffer("Java");

System.out.println("원본 문자열 : " + str);  //원본 문자열 : Java

System.out.println(str.append("수업")); //Java수업

System.out.println("append() 메소드 호출 후 원본 문자열 : " + str);  //Java수업
```

- capacity() 메소드

capacity() 메소드는 StringBuffer 인스턴스의 현재 버퍼 크기를 반환합니다.

```
StringBuffer str01 = new StringBuffer();

StringBuffer str02 = new StringBuffer("Java");

System.out.println(str01.capacity()); //16

System.out.println(str02.capacity()); //20
```

길이가 4인 문자열로 StringBuffer 인스턴스를 생성하면, 기본적으로 생성되는 여유 버퍼 크기인 16에 문자의 길이인 4를 더한 총 20개의 문자를 저장할 수 있는 버퍼가 생성

- delete(인덱스, 인덱스) 메소드

delete() 메소드는 전달된 인덱스에 해당하는 부분 문자열을 해당 문자열에서 제거합니다.

첫 번째 매개변수로 전달된 인덱스부터 두 번째 매개변수로 전달된 인덱스 바로 앞의 문자까지를 삭제

또한, deleteCharAt() 메소드를 사용하면 특정 위치의 문자 한 개만을 제거할 수도 있습니다.

```
StringBuffer str = new StringBuffer("Java Oracle");

System.out.println("원본 문자열 : " + str);  //원본 문자열 : Java Oracle

① System.out.println(str.delete(4, 8)); //Javacle, delete() 메소드를 사용하여 해당 문자열에서 인덱스가 4인 위치의 문자부터 7인 위치의 문자까지를 삭제

System.out.println(str.deleteCharAt(1));  //Jvacle

System.out.println("deleteCharAt() 메소드 호출 후 원본 문자열 : " + str);  //deleteCharAt() 메소드 호출 후 원본 문자열 : Jvacle
```

- insert(인덱스, 값) 메소드

insert() 메소드는 인수로 전달된 값을 문자열로 변환한 후, 해당 문자열의 지정된 인덱스 위치에 추가합니다.

이때 전달된 인덱스가 해당 문자열의 길이와 같으면, append() 메소드와 같은 결과를 반환합니다.

```
StringBuffer str = new StringBuffer("Java 만세!!"); 

System.out.println("원본 문자열 : " + str);  //원본 문자열 : Java 만세!!

① System.out.println(str.insert(4, "Script"));  //JavaScript 만세!!

System.out.println("insert() 메소드 호출 후 원본 문자열 : " + str);  //insert() 메소드 호출 후 원본 문자열 : JavaScript 만세!!
```

- reverse() 메소드

글자 순서를 뒤집는다.

## 참고 

<http://www.tcpschool.com/java/java_api_stringBuffer>

<https://wakestand.tistory.com/245>
