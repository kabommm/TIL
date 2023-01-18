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


## 참고
<https://st-lab.tistory.com/92>
