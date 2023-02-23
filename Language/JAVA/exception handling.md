# 예외 처리

```
try {

    예외를 처리하길 원하는 실행 코드;

} catch (e1) {

    e1 예외가 발생할 경우에 실행될 코드;

} catch (e2) {

    e2 예외가 발생할 경우에 실행될 코드;

}

...

finally {

    예외 발생 여부와 상관없이 무조건 실행될 코드;

}
```

catch 블록과 finally 블록은 선택적인 옵션으로 반드시 사용할 필요는 없습니다.

따라서 사용할 수 있는 모든 적합한 try 구문은 다음과 같습니다.

1. try / catch

2. try / finally

3. try / catch / ... / finally

```
try {

    System.out.write(list);

} catch (Exception e) {

    e.printStackTrace();

} catch (IOException e) {

    e.printStackTrace();

}
```

IOException은 Exception의 자식 클래스이므로, 첫 번째 catch 블록에서도 IOException을 처리할 수 있습니다.

따라서 IOException을 비롯한 Exception 클래스의 자식 클래스에 해당하는 예외가 발생하면, 언제나 첫 번째 catch 블록에서만 처리될 것입니다.

즉, catch 블록의 순서를 위의 예제처럼 작성하면, 두 번째 catch 블록은 영원히 실행되지 못할 것입니다.

따라서 IOException만을 따로 처리하고자 한다면, 다음 예제처럼 catch 블록의 순서를 변경해야 합니다.

```
try {

    System.out.write(list);

} catch (IOException e) {

    e.printStackTrace();

} catch (Exception e) {

    e.printStackTrace();

}
```

위의 예제에서 IOException이 발생하면, 첫 번째 catch 블록에서 해당 예외를 처리할 것입니다.

또한, IOException 외의 Exception 클래스의 자식 클래스에 해당하는 예외가 발생하면, 두 번째 catch 블록에서 처리될 것입니다.

이처럼 범위가 더 좁은 예외를 처리하는 catch 블록을 먼저 명시하고, 범위가 더 넓은 예외를 처리하는 catch 블록은 나중에 명시해야만 정상적으로 해당 예외를 처리할 수 있습니다.

## 여러 예외 타입의 try {

```
    this.db.commit();

} catch (IOException | SQLException e) {

    e.printStackTrace();

}
```

하지만 둘 이상의 예외 타입를 동시에 처리하는 catch 블록에서 매개변수로 전달받은 예외 객체는 묵시적으로 final 제어자를 가지게 됩니다.

따라서 catch 블록 내에서 해당 매개변수에는 어떠한 값도 대입할 수 없습니다.

## Throwable 클래스

자바에서 Throwable 클래스는 모든 예외의 조상이 되는 Exception 클래스와 모든 오류의 조상이 되는 Error 클래스의 부모 클래스입니다.

Throwable 타입과 이 클래스를 상속받은 서브 타입만이 자바 가상 머신(JVM)이나 throw 키워드에 의해 던져질 수 있습니다.

![](https://github.com/kabommm/TIL/blob/main/Language/img/Throwable.PNG)

다음 예제는 일부러 숫자를 0으로 나눠 ArithmeticException 오류를 발생시키는 예제입니다.

이렇게 발생한 오류에 대해 Throwable 메소드를 사용하여 발생한 오류에 대한 정보를 출력합니다.

```
try {

    System.out.println(5 / 0);

} catch (ArithmeticException e) {

    System.out.println("현재 발생한 예외 정보 : " + e.getMessage());

}
```

## 자주 사용되는 예외 클래스

![](https://github.com/kabommm/TIL/blob/main/Language/img/Exception.PNG)

## 예외 발생 및 회피

- 예외 발생시키기
- 
자바에서는 throw 키워드를 사용하여 강제로 예외를 발생시킬 수 있습니다.

```
Exception e = new Exception("오류메시지");

...

throw e;
```

- 예외 회피하기

메소드 선언부에 throws 키워드를 사용하여 해당 메소드를 사용할 때 발생할 수 있는 예외를 미리 명시할 수도 있습니다.

이렇게 하면 해당 메소드를 사용할 때 발생할 수 있는 예외를 사용자가 충분히 인지할 수 있으며, 그에 대한 처리까지도 강제할 수 있습니다.

```
public class Exception03 {

    static void handlingException() {

        try {

            throw new Exception();

        } catch (Exception e) {

            System.out.println("호출된 메소드에서 예외가 처리됨!");

        }

    }

 

    public static void main(String[] args) {

        try {

            handlingException();

        } catch (Exception e) {

            System.out.println("main() 메소드에서 예외가 처리됨!");

        }

    }

}
```



## 참고

<http://tcpschool.com/java/java_exception_class>
