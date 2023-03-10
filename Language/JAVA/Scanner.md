# Scanner 클래스

## 특징
- 기본적인 데이터 타입들을 Scanner 의 메소드를 사용하여 입력받을 수 있다.
예로 들어 100을 입력하고자 할 때, String(문자열)로 입력받고 싶으면 next() 나 nextLine() 을, int(정수)로 입력받고 싶다면 nextInt() 를 사용하여 입력받으면 알아서 해당 타입으로 입력된다.

- Scanner 을 사용할 시 util 패키지를 경로의 Scanner 클래스를 호출해야 한다.
import java.util.Scanner; 추가

- 공백(띄어쓰기) 또는 개행(줄 바꿈)을 기준으로 읽는다.
Scanner 의 입력 메소드들은 대부분 공백과 개행(' ', '\t', '\r', '\n' 등등..)을 기준으로 읽는다. 이 덕분에 사용자의 편의에 따라 쉽게 입력을 받을 수 있다.

```
import java.util.Scanner;	// Scanner 클래스 호출

Scanner sc = new Scanner(System.in); // Scanner 객체 생성

    byte a = sc.nextByte(); 		// byte 형 입력 및 리턴
		short b = sc.nextShort(); 		// short 형 입력 및 리턴
		int c = sc.nextInt(); 			// int 형 입력 및 리턴
		long d = sc.nextLong(); 		// long 형 입력 및 리턴
 
		float e = sc.nextFloat(); 		// float 형 입력 및 리턴
		double f = sc.nextDouble(); 	// double 형 입력 및 리턴
 
		boolean g = sc.nextBoolean(); 	// boolean 형 입력 및 리턴
 
		String h = sc.next(); 			// String 형 입력 및 리턴 (공백을 기준으로 한 단어를 읽음)
		String i = sc.nextLine(); 		// String 형 입력 및 리턴 (개행을 기준으로 한 줄을 읽음)
```

System.in 은 사용자로부터 입력을 받기 위한 입력 스트림이다.

## Escape Sequence

print 즉, 출력할 때 큰 따옴표 ( " ) 나 백슬래시 ( \ ) 는 단독으로 써서 출력할 수가 없다.

그래서 이를 출력하기 위해 특정 구문을 사용하는데 이를 이스케이프 한다고 말한다.

그리고 결합된 그 문자를 Escape Sequence  라고 하는데 백슬래시 ( \ ) 와 문자 하나를 결합하여 나타낸다.

우리가 흔히 쓰는 \n \t  같은 것도 이스케이프 시퀀스다.

( 이스케이프 시퀀스 = 이스케이프 문자 = 제어문자 .. 모두 같은 말이다. )

즉, 백슬래시를 출력하려면  ( " \\ " ) 로 해줘야 백슬래시 ( \ ) 하나가 출력되며, 백슬래시 두 개를 출력하고 싶은경우 ( " \\\\ " ) 로 해주어야 2개가 출력된다. 

아래 그림은 자바에서 사용하는 표준 문자열 이스케이프 리스트다.

![](https://github.com/kabommm/TIL/blob/main/Language/img/Escape%20Sequence.png)

사용예제 문제: <https://www.acmicpc.net/problem/10172>

## 참고

<https://st-lab.tistory.com/92>

Escape Sequence: <https://st-lab.tistory.com/11>
