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
