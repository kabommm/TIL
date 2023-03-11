# I/O 클래스

파일이나 통신 등 디지털 정보의 입출력을 처리하는 클래스가 정의된 패키지

## I/O 클래스의 인터페이스

java.io에 정의된 인터페이스와 클래스 명칭을 보면 바이트 단위 입출력을 수행하는 클래스는 이름이 Stream 으로 끝나고,
문자열 단위 입출력을 수행하는 클래스는 Reader/Writer 로 끝나는 것이 일반적이다.
클래스 명칭에 File, Data, Buffered 와 같은 접두어가 붙게 되면 해당 클랙스가 사용하는 입출력 데이터의 종류를 알 수가 있다.

- Stream으로 끝나는 클래스 : 바이트 단위로 입출력을 수행하는 클래스

- Reader / Writer로 끝나는 클래스 : 캐릭터 단위로 입출력을 수행하는 클래스

- File로 시작하는 클래스 : 하드디스크의 파일을 사용하는 클래스

- Data로 시작하는 클래스 : 자바의 원시 자료형을 출력하기 위한 클래스

- Buffered로 시작하는 클래스 : 시스템의 버퍼를 사용하는 클래스

> 1차 스트림 : 입/출력 통로를 직접 만드는 클래스

> 2차 스트림 : 기존의 통로를 이용하여 새로운 기능을 더하는 클래스

## InputStream / OutputStream (바이트 입출력)

- 바이트, 바이트 배열, 정수, 데이터 등의 흐름 

- 8bit(=1byte) 크기의 스트림들에 대한 입출력

## InputStream

![](https://github.com/kabommm/TIL/blob/main/Language/img/InputStream.PNG)

## OutputStream

![](https://github.com/kabommm/TIL/blob/main/Language/img/OutputStream.PNG)

## Reader / Writer (문자 입출력)

- 문자, 문자 배열, 문자열 등의 흐름

- 16bit(=2byte) 크기의 유니코드 문자들의 입출력

## Reader

![](https://github.com/kabommm/TIL/blob/main/Language/img/Reader.PNG)

## Reader 메소드

![](https://github.com/kabommm/TIL/blob/main/Language/img/Reader%20Method.PNG)

- readLine()

  BufferedReader는 readLine()메소드를 가집니다.
  
  readLine메서드는 텍스트를 한 줄씩 읽어 String형의 반환 값으로 돌려줍니다.

## Writer

![](https://github.com/kabommm/TIL/blob/main/Language/img/Writer.PNG)

## Writer 메소드

![](https://github.com/kabommm/TIL/blob/main/Language/img/Writer%20Method.PNG)

## 그외의 java.io 클래스

![](https://github.com/kabommm/TIL/blob/main/Language/img/ect.PNG)


## 참고

<https://repilria.tistory.com/400>

<http://www.incodom.kr/java/java.io>

Reader/Writer 메소드: <https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=qbxlvnf11&logNo=221140609067>
