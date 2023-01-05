# Thymeleaf

-

## Thymeleaf를 사용하는 이유

- JSP와 유사하게 ${}을 별도의 처리 없이 이용할 수 있습니다.
- Model에 담긴 객체를 화면에서 JavaScript로 처리하기 편리합니다.
- 연산이나 포맷과 관련된 기능을 추가적인 개발 없이 지원합니다.
- 개발 도구를 이용할 때 .html 파일로 생성하는데 문제가 없고 별도의 확장자를 이용하지 않습니다.

# Thymeleaf 사용

- Thymeleaf 적용을 위해서는 html 태그를 다음과 같이 해야한다.

```
<html lang="en" xmlns:th="http://www.thymeleaf.org">
```

- 속성
  기존의 속성 앞에 'th:'를 붙여주고 속성값을 지정한다.
- 반복
  th:each라는 속성을 이용한다.
  state는 상태 객체로 순번이나 인덱스 번호, 홀수/짝수 등을 지정할 수 있다.

```
<li th:each = "dto, state : ${list} ">  //dto는 변수이고 'list'은 controller에서 Model로 전달된 데이터
    [[${state.index}]] --- [[${dto}]]  //[[]]은 별도의 태그 속성으로 지정하지 않고 사용할 때 사용
</li>
```

- 제어문
  th:if ~unless를 이용하거나 삼항연산자 스타일을 사용할 수 있다.
  - th: if
  ```
  <li th:each = "dto, state : ${list} " th:if="${dto.sno % 5 == 0}">  //dto는 변수이고 'list'은 controller에서 Model로 전달된 데이터
      [[${dto}]]  //[[]]은 별도의 태그 속성으로 지정하지 않고 사용할 때 사용
  </li>
  ```
  - th:if ~ unless
    Thymeleaf에서는 if~else가 단독으로 처리된다.
  ```
  <li th:each = "dto, state : ${list} ">
      < span th:if="${dto.sno % 5 == 0}" th:text="${'-----------'+dto.sno}"></span>
      < span th:unless="${dto.sno % 5 == 0}" th:text="${dto.first}"></span>
  </li>
  ```
  - 삼항연산자
  ```
  <li th:each = "dto, state : ${list} " th:text="${dto.sno % 5 == 0} ?  ${dto.sno} : ${dto.first}">
  </li>
  ```
- th:block
  블록은 실체화면에서는 html로 처리되지 않기 때문에 루프 등을 별도로 처리하는 용도로 많이 사용된다.
  ```
  <th:block th:each="dto: ${list}">
      <li th:text="${dto.sno % 5 == 0} ?  ${dto.sno} : ${dto.first}">
      </li>
  </th:block>
  ```
- 링크 처리
  '@{}'를 이욯해서 사용한다.

```
<li th:each = "dto : ${list} ">
    <a th:href="@{/sample/exView/{sno}(sno=${dto.sno})}">[[${dto}]]</a>
</li>
```

- Thymeleaf의 기본 객체와 LocalDateTime
  #numbers #dates 등을 별도의 설정 없이 사용할 수 있다.

sno를 모두 5자리로 나타내는 경우

```
<li th:each = "dto : ${list} ">
    [[${#numbers.formatInteger(dto.sno,5)}]]
</li>
```

날짜 표현, build.gradle에 의존성 추가 필요
의존성 추가 코드

```
compile group: 'org.thymeleaf.extras', name: 'thymeleaf-extras-java8time'
```

html코드

```
<li th:each = "dto : ${list} ">
    [[${#temporals.format(dto.regTime, 'yyyy/MM/dd')}]]
</li>
```
