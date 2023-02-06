# String 클래스

String 인스턴스는 한 번 생성되면 그 값을 읽기만 할 수 있고, 변경할 수는 없습니다.

 java.lang 패키지에 포함

## 메소드

-charAt

해당 문자열의 특정 인덱스에 해당하는 문자를 반환

- compareTo

두 개의 string을 앞에서부터 순차적으로 비교하다가 두 문자열이 같다면 0을 반환하며, 해당 문자열이 인수로 전달된 문자열보다 작으면 음수를, 크면 양수를 반환합니다.

대소문자를 구분하여 비교합니다. 아스키코드의 값을 기준으로 비교

만약 두 문자열이 같다면 0을 반환하며, 해당 문자열이 인수로 전달된 문자열보다 작으면 음수를, 크면 양수를 반환합니다.

대소문자를 구분하지 않기를 원한다면, compareToIgnoreCase() 메소드를 사용

기준이 되는 아스키코드 - 비교되는 아스키코드

```
String str = new String("abcd");

System.out.println("원본 문자열 : " + str);  //원본 문자열 : abcd

System.out.println(str.compareTo("bcef"));  //-1

System.out.println(str.compareTo("abcd") + "\n"); //0

System.out.println(str.compareTo("Abcd"));  //32

System.out.println(str.compareToIgnoreCase("Abcd"));  //0, 대소문자 구분x
```

- concat

해당 문자열의 뒤에 인수로 전달된 문자열을 추가한 새로운 문자열을 반환

```
String str1 = "안녕 !"; 
String str2 = "나는 호준이야."; 
String concat = str1.concat(str2); 
System.out.println(concat);	// 안녕 ! 나는 호준이야.
```

- startWith

문자열이 지정한 문자로 시작하는지 체크하여 맞을 경우 true를 맞지 않을 경우 false를 반환한다. 대소문자를 구별!!

```
String str1 = "김호준";
String str2 = "abcde";

System.out.println(str1.startWith("김"));	// true
System.out.println(str1.startWith("호"));	// false
System.out.println(str2.startWith("A"));	// false, 대소문자 구분
```

- endWith

문자열의 마지막에 지정한 문자가 있는지 체크하여 있다면 true를 없다면 false를 반환한다. 대소문자를 구별!!

```
String s = "I have a book";
System.out.println(s.endsWith("book")); 	// true
System.out.println(s.endsWith("a")); 		// false
```

- indexOf

해당 문자열에서 특정 문자나 문자열이 처음으로 등장하는 위치의 인덱스를 반환

만약 해당 문자열에 전달된 문자나 문자열이 포함되어 있지 않으면 -1을 반환

```
String str1 = "문자열을 공부해보자";
String str2 = "abcedf";

System.out.println(str1.indexOf("공부"));	// 5
System.out.println(str2.indexOf("b"));		// 1
```

- trim

해당 문자열의 맨 앞과 맨 뒤에 포함된 모든 공백 문자를 제거

중요한 점은 문자열 중간의 공백은 제거하지 않는다

```
String str1 = "     김  호준     ";
System.out.println(str1.trim());		// 김   호준
```

- toLowerCase()와 toUpperCase()

toLowerCase() 메소드는 해당 문자열의 모든 문자를 소문자로 변환시켜 줍니다.

또한, toUpperCase() 메소드는 해당 문자열의 모든 문자를 대문자로 변환시켜 줍니다.

```
String str = new String("Java");

System.out.println(str.toLowerCase());  //java

System.out.println(str.toUpperCase());  //JAVA
```

- split

지정한 문자로 문자열을 나눌 때 사용한다.

나눠진 문자열은 배열로 반환되어 배열에 저장된다

```
String str = "A:B:C:D:ab:cd"; 
String[] split = str.split(":");

System.out.println(split[1]);		// B
System.out.println(split[2]);		// C
System.out.println(split[4]);		// ab
System.out.println(split[5]);		// cd
```

- substring

문자열 중 특정 부분을 뽑아낼 경우에 사용한다.

매개변수에 1개를 입력할 경우: 시작지점으로 인식하여 시작지점부터 해당 문자열의 끝까지 출력

매개변수에 2개를 입력할 경우: 시작지점과 끝지점으로 인식하여 출력(주의: 끝지점 전의 인덱스까지 반환)

```
String str = "ABCDEF"; 
String substring1 = str.substring(0, 2); 
String substring2 = str.substring(1); 
System.out.println("substring1: " + substring1);	// substring1: AB
System.out.println("substring2: " + substring2);	// substring2: BCDEF
```

- length

해당 문자열의 길이를 반환함

```
String str = "abcdef"; 
int length = str.length(); 
System.out.println(length);	// 6
```

- isEmpty

해당 문자열의 길이가 0이면 true를 반환하고, 아니면 false를 반환함.

- equals

두개의 문자열이 동일한 값을 가지고 있는지 비교하여 결과값을 리턴

여기서 중요한 것은 a==b는 문자열 변수의 주소값을 비교하는 것이고 a.eqauls(b)는 문자열이 가지고 있는 값 자체를 비교한다는 것이다.

```
String a = "banana";
String d = new String("banana");

System.out.println(a==d);		//false, 값이 같으나 주소가 다름
System.out.println(a.equals(d));	//true, 값 자체가 같다
```

- replaceAll
문자열 중 특정 문자를 다른 문자로 바꾸고 싶을 때 사용한다.

replace와는 다르게 정규표현식을 지정한 문자로 바꿔서 출력한다

```
String str1 = "문자열을 공부하자. 화이팅!"; 
System.out.println(str1.replaceAll("문자열", "자료구조를"));	// "문자열" -> "자료구조를"
```

- replace

문자열에 특정한 문자를 원하는 문자로 변경하고 싶을 경우에 사용한다. replace(기존 문자열, 새로바꿀 문자열) 의 형태
```
        String str = "c#cake";
        System.out.println( str.replace("#","%") ); //  c%cake
```

### replace vs replaceAll
replace는 첫번째 인자값에 문자열이 들어가 문자열만 변경 가능하지만 replaceAll은 첫번째 인자값에 정규식이 들어가 문자열 뿐만아니라 정규식도 적용이 가능하다.

```
String allTest = "aaabbbvccacfgdracabtghd";
        System.out.println( allTest.replace("ab","0") );  //  aa0bbvccacfgdrac0tghd

        System.out.println( allTest.replaceAll("[ab]","0") ); //  000000vcc0cfgdr0c00tghd
```

-replaceFirst

사용법은 위와 전부 같으나 First라는 것을 보고 알 수 있듯이 처음 나오는 단어를 찾아서 바꿔주는 함수이다.
```
String replaceFirstTest = "우리의 리플레이스의 리플레이스테스트";

System.out.println( replaceFirstTest.replaceFirst("리플레이스","replaceFirst") );  //  우리의 replaceFirst의 리플레이스테스트
```

- contains
두개의 문자열을 비교하여 비교대상 String을 포함하고 있으면 true를 포함하고 있지 않다면 false를 반환한다.

공백, 대/소문자를 구분한다.

```
        String str = "my java test";

        System.out.println( str.contains("java") );  // true
        System.out.println( str.contains(" my") );  // false, 공백
        System.out.println( str.contains("JAVA") );  // false, 대소문자
        System.out.println( str.contains("java test") );  // true
```

- repeat
문자열을 반복하는 메소드

```
public class Repeat {
	public static void main(String[] args) {
		// String 및 StringBuilder 호출
		String str = "Hello";
		StringBuilder sb = new StringBuilder();
		
		// 반복문을 사용하여 문자열 반복
		for(int i = 0; i < 3; i++)
		{
			sb.append(str);
		}
		
		// 결과 출력 -> for문
		System.out.println("for문 : " + sb);
		// 결과 출력 -> repeat 사용
		System.out.println("repeat문 : " + str.repeat(3));
	}
}
```

for문을 통해 문자열을 반복하는방법과 repeat로 반복하는 방법 두가지를 예시로 들었다.

## 참고
<https://velog.io/@rlaghwns1995/Java-String-%EA%B4%80%EB%A0%A8-%EB%82%B4%EC%9E%A5%ED%95%A8%EC%88%98>
<https://cceeun.tistory.com/32>
<https://mine-it-record.tistory.com/127>
<http://www.tcpschool.com/java/java_api_string>
