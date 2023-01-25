# 래퍼 클래스

기본 타입에 해당하는 데이터를 객체로 포장해 주는 클래스

Wrapper 클래스는 java.lang 패키지에 포함

- 박싱(Boxing)과 언박싱(UnBoxing)

![](https://github.com/kabommm/TIL/blob/main/Language/img/box.png)

위의 그림과 같이 기본 타입의 데이터를 래퍼 클래스의 인스턴스로 변환하는 과정을 박싱(Boxing)이라고 합니다.

반면 래퍼 클래스의 인스턴스에 저장된 값을 다시 기본 타입의 데이터로 꺼내는 과정을 언박싱(UnBoxing)이라고 합니다.

- 오토 박싱(AutoBoxing)과 오토 언박싱(AutoUnBoxing)

자동화된 박싱과 언박싱을 오토 박싱(AutoBoxing)과 오토 언박싱(AutoUnBoxing)이라고 부릅니다.

```
Integer num = new Integer(17); // 박싱
int n = num.intValue();        // 언박싱
System.out.println(n);      //17

Character ch = 'X'; // Character ch = new Character('X'); : 오토박싱
char c = ch;        // char c = ch.charValue();           : 오토언박싱
System.out.println(c);      //c
```

## 참고
<http://www.tcpschool.com/java/java_api_wrapper>
