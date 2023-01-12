# Character 클래스

- 문자 데이터에 대한 다양한 처리를 위한 상수 및 메서드 제공

## isXXX() 메서드 : 특정 대상인지 여부 판별

ch 는 대문자인가? " + Character.isUpperCase(ch)

ch 는 소문자인가? " + Character.isLowerCase(ch)

"ch 는 문자인가? " + Character.isLetter(ch)

"ch 는 숫자인가? " + Character.isDigit(ch)

"ch 는 공백문자인가? " + Character.isWhitespace(ch)

## toXXX() 메서드 : 특정 대상 타입으로 변환

ch + " -> 대문자로 변환 : " + Character.toUpperCase(ch)

ch + " -> 소문자로 변환 : " + Character.toLowerCase(ch)

## char -> String 타입 변환

String str = Character.toString(ch);

## 참고
<https://itellyhood.tistory.com/71>
