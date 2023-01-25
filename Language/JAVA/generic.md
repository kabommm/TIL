# 제네릭

제네릭(generic)이란 데이터의 타입(data type)을 일반화한다(generalize)는 것을 의미

제네릭은 클래스나 메소드에서 사용할 내부 데이터 타입을 컴파일 시에 미리 지정하는 방법

## 제네릭의 선언 및 생성

```
class MyArray<T> {
    T element;
    void setElement(T element) { this.element = element; }
    T getElement() { return element; }

}
```

위의 예제에서 사용된 'T'를 타입 변수(type variable)라고 하며, 임의의 참조형 타입을 의미합니다.

꼭 'T'뿐만 아니라 어떠한 문자를 사용해도 상관없으며, 여러 개의 타입 변수는 쉼표(,)로 구분하여 명시할 수 있습니다.

타입 변수는 클래스에서뿐만 아니라 메소드의 매개변수나 반환값으로도 사용할 수 있습니다. 

```
MyArray<Integer> myArr = new MyArray<Integer>();
```

위의 예제는 MyArray 클래스에 사용된 타입 변수로 Integer 타입을 사용하는 예제입니다.

위처럼 제네릭 클래스를 생성할 때 사용할 실제 타입을 명시하면, 내부적으로는 정의된 타입 변수가 명시된 실제 타입으로 변환되어 처리됩니다.

또한, Java SE 7부터 인스턴스 생성 시 타입을 추정할 수 있는 경우에는 타입을 생략할 수 있습니다.

```
MyArray<Integer> myArr = new MyArray<>(); // Java SE 7부터 가능함.
```
