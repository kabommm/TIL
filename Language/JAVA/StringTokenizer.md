# StringTokenizer 클래스

BufferedReader 클래스의 메서드로 입력을 읽어들이면, 라인 단위로 읽어들일 수밖에 없다.

BufferedReader 클래스가 아니더라도, 특정 문자에 따라 문자열을 나누고 싶을 때 StringTokenizer사용

String:문자열을 Tokenizer:토큰화한다. 즉 토큰은 분리된 문자열 조각으로, 하나의 문자열을 여러 개의 토큰으로 분리하는 클래스

## StringTokenizer 임포트

```
import java.util.StringTokenizer;
```

## StringTokenizer 생성자

3가지 방식이 있다.

1.

```
StringTokenizer st = new StringTokenizer(문자열);  //띄어쓰기 기준으로 분리
```

```
import java.util.StringTokenizer;
public class Main {
    public static void main(String[] args) {
        String str = "하나 둘 셋 넷";
        StringTokenizer st = new StringTokenizer(str);
        
        System.out.println(st.nextToken()); //하나
        System.out.println(st.nextToken()); //둘
        System.out.println(st.nextToken()); //셋
        System.out.println(st.nextToken()); //넷
    }
}
```

분리된 문자열(토큰)을 확인하고 싶으면 nextToken() 사용

2.

```
StringTokenizer st new StringTokenizer(문자열,구분자);  //구분자를 기준으로 분리
```

3.

```
StringTokenizer st = new StringTokenizer(문자열,구분자,true/false); //구분자를 기준으로 분리할 때 구분자도 토큰으로 넣을지(true) 구분자는 분리된 문자열 토큰에 포함
안시킬지(false) (디폴트는 false)
```

```
import java.util.StringTokenizer;
public class Main {
    public static void main(String[] args) {
        String str = "일!이!삼";
        StringTokenizer st = new StringTokenizer(str, "!", true);
        
        int i = 1;
        while(st.hasMoreTokens()){
          System.out.println((i++)+"번째 토큰: " + st.nextToken()); //true를 넣어주었으므로 2번째 줄에 2번째 토큰: ! 와 4번째 줄에 4번째 토큰! 출력
        }
    }
}
```

## 여러 문자를 구분자로 사용하기

```
import java.util.StringTokenizer;
public class Main {
    public static void main(String[] args) {
        String str = "안녕!반가~워";
        StringTokenizer st = new StringTokenizer(str, "!~");

        while(st.hasMoreTokens()){
          System.out.println(st.nextToken());
        }
    }
}
```
 
## StringTokenizer vs split

둘 다 문자열을 파싱하는데 사용되지만 다음과 같은 차이점이 있다.

- StringTokenizer는 java.util에 포함되어 있는 클래스(따로 impport 선언 필요), split은 String 클래스에 속해있는 메소드(기본 내장)

- StringTokenizer는 문자 또는 문자열로 구분하지만 split은 정규 표현식으로 구분

- StringTokenizer는 빈 문자열을 토큰으로 인식하지 않지만 split은 빈 문자열을 토큰으로 인식

- StringTokenizer는 결과값이 문자열이지만 split은 결과값이 문자열 배열

## 참고

<https://jhnyang.tistory.com/398>
