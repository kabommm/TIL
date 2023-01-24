# Object 클래스

java.lang.Object 클래스는 자바에서 제공하는 모든 클래스들의 최상위 클래스이므로 자바에서 제공하는 클래스뿐만 아니라 사용자가 정의한 클래스도 Object클래스가 제공하는 매서드를 상속 받아서 사용할 수 있다.

## toString()

toString() 메소드는 해당 인스턴스에 대한 정보를 문자열로 반환합니다.

## Object clone()

객체를 복제하는데 사용한다.

## boolean equals(Object object)

두개의 객체가 같은지를 비교해서 같으면 true, 다르면 flase를 리턴한다.

## void finalize()

가비지 컬렉션 기능이 수행하기 전에 호출되며 객체가 점유했던 자원들을 해제한다.

## Class getClass()

객체의 클래스명을 Class형의 객체로 리턴한다.

## int hashCode()

호출한 객체와 연관된 hash 코드를 리턴한다.

## void notify()

대기중인 스레드 중 하나의 스레드를 다시 시작한다.

## void notifyAll()

대기중인 모든 스레드를 다시 시작시킨다.

## void wait()

실행을 중지하고 대기 상태로 간다.

## 참고
<https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=reach_reach&logNo=90119089674>
<http://www.tcpschool.com/java/java_api_object>
