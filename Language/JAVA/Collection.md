# 컬렉션 프레임워크

다수의 데이터를 쉽고 효과적으로 처리할 수 있는 표준화된 방법을 제공하는 클래스의 집합

즉, 데이터를 저장하는 자료 구조와 데이터를 처리하는 알고리즘을 구조화하여 클래스로 구현해 놓은 것입니다.

이러한 컬렉션 프레임워크는 자바의 인터페이스(interface)를 사용하여 구현됩니다.

- 컬렉션 프레임워크 주요 인터페이스

데이터를 저장하는 자료 구조에 따라 다음과 같은 핵심이 되는 주요 인터페이스를 정의하고 있습니다.

1. List 인터페이스

2. Set 인터페이스

3. Map 인터페이스

![](https://github.com/kabommm/TIL/blob/main/Language/img/interface.PNG)

![](https://github.com/kabommm/TIL/blob/main/Language/img/collection.PNG)

컬렉션 프레임워크의 모든 컬렉션 클래스는 List와 Set, Map 인터페이스 중 하나의 인터페이스를 구현하고 있습니다.

![](https://github.com/kabommm/TIL/blob/main/Language/img/Collection.png)

형태에 따라서는 크게 List(리스트), Queue(큐), Set(집합)으로 나뉘어 있다.

## List 컬렉션 클래스

List 인터페이스는 배열과 같이 공통되 특성을 묶지만 배열에서는 배열의 크기를 변경할 수 없으며 삽입, 삭제가 유용하지 않다.
하지만 List는 데이터의 개수에 따라 메모리를 동적 할당해주고 주소로 데이터들이 연결되어 있어 삽입, 삭제에 유용하기 때문에 삽입, 삭제가 필요시 사용하기 좋다.

데이터들이 연속적으로 나열되고 데이터 사이에 빈 공간을 허락하지 않는다. 배열에서는 데이터를 삭제하면 데이터 사이에 빈공간이 생겨 null뒤의 데이터를 한칸씩 끌어와야 한다.
이는 속도가 느려 삽입, 삭제가 빈번한 경우 유용하기 않기 때문에 List를 사용한다.

대표적인 List 컬렉션 클래스에 속하는 클래스는 다음과 같습니다.

1. ArrayList`<E>`

2. LinkedList`<E>`

3. Vector`<E>`

4. Stack`<E>`
  
### ArrayList`<E>` 클래스

  데이터의 개수를 알 수 없는데 배열을 쓰고 싶을 때 사용
  
  내부적으로 배열을 이용하여 요소를 저장합니다.
  
  - 생성
  
  ```
  ArrayList<Integer> arrList = new ArrayList<Integer>();
  ```
  
### LinkedList`<E>` 클래스
  
  ArrayList 클래스가 배열을 이용하여 요소를 저장함으로써 발생하는 단점을 극복하기 위해 고안
  
  내부적으로 연결 리스트(linked list)를 이용하여 요소를 저장
  
  연결 리스트는 저장된 요소가 비순차적으로 분포되며, 이러한 요소들 사이를 링크(link)로 연결하여 구성
  다음 요소를 가리키는 참조만을 가지는 연결 리스트를 단일 연결 리스트(singly linked list)라고 합니다.
  
  단일 연결 리스트는 요소의 저장과 삭제 작업이 다음 요소를 가리키는 참조만 변경하면 되므로, 아주 빠르게 처리될 수 있지만 현재 요소에서 이전 요소로 접근하기가 매우 어렵습니다.

  따라서 이전 요소를 가리키는 참조도 가지는 이중 연결 리스트(doubly linked list)가 좀 더 많이 사용됩니다.
  
  LinkedList 클래스도 위와 같은 이중 연결 리스트를 내부적으로 구현한 것입니다.

  또한, LinkedList 클래스 역시 List 인터페이스를 구현하므로, ArrayList 클래스와 사용할 수 있는 메소드가 거의 같습니다.
  
  - 생성
  
  ```
  LinkedList<String> lnkList = new LinkedList<String>();
  ```

### Vector`<E>` 클래스
  
Vector 클래스에서 사용할 수 있는 메소드도 ArrayList 클래스에서 사용할 수 있는 메소드와 거의 같습니다.

하지만 현재에는 기존 코드와의 호환성을 위해서만 남아있으므로, Vector 클래스보다는 ArrayList 클래스를 사용하는 것이 좋습니다.

## List 인터페이스 메소드

List 인터페이스는 Collection 인터페이스를 상속받으므로, Collection 인터페이스에서 정의한 메소드도 모두 사용할 수 있습니다.
![](https://github.com/kabommm/TIL/blob/main/Language/img/list.PNG)

### Stack`<E>` 클래스

Stack 클래스는 List 컬렉션 클래스의 Vector 클래스를 상속받아, 전형적인 스택 메모리 구조의 클래스를 제공합니다.

후입선출(LIFO)- 가장 나중에 저장된(push) 데이터가 가장 먼저 인출(pop)

Stack 클래스는 스택 메모리 구조를 표현하기 위해, Vector 클래스의 메소드를 5개만 상속받아 사용합니다.

## Stack`<E>` 클래스 메서드
![](https://github.com/kabommm/TIL/blob/main/Language/img/stack.PNG)

## Queue`<E>` 인터페이스

클래스로 구현된 스택과는 달리 자바에서 큐 메모리 구조는 별도의 인터페이스 형태로 제공됩니다.

선입선출(FIFO)- 가장 먼저 저장된(push) 데이터가 가장 먼저 인출(pop)

이러한 Queue 인터페이스를 상속받는 하위 인터페이스는 다음과 같습니다.

1. Deque`<E>`

2. BlockingDeque`<E>`

3. BlockingQueue`<E>`

4. TransferQueue`<E>`
  
Deque 인터페이스를 구현한 LinkedList 클래스가 큐 메모리 구조를 구현하는 데 가장 많이 사용됩니다.

## Queue`<E>` 인터페이스 메서드
![](https://github.com/kabommm/TIL/blob/main/Language/img/Queue.PNG)

## Set 컬렉션 클래스

Set(세트)는 말 그대로 '집합'이다. 데이터 중복 저장x,  입력 순서대로의 저장 순서를 보장하지 않는다.
  
1. HashSet`<E>`

2. TreeSet`<E>`
  
### HashSet`<E>` 클래스
  
  해시 알고리즘(hash algorithm)을 사용하여 검색 속도가 매우 빠르고 내부적으로 HashMap 인스턴스를 이용하여 요소를 저장
  
  이때 해당 HashSet에 이미 존재하는 요소인지를 파악하기 위해서는 내부적으로 다음과 같은 과정을 거치게 됩니다.

  1. 해당 요소에서 hashCode() 메소드를 호출하여 반환된 해시값으로 검색할 범위를 결정합니다.

  2. 해당 범위 내의 요소들을 equals() 메소드로 비교합니다.
  
  - 해시 알고리즘(hash algorithm)
  
  해시 알고리즘(hash algorithm)이란 해시 함수(hash function)를 사용하여 데이터를 해시 테이블(hash table)에 저장하고, 다시 그것을 검색하는 알고리즘입니다.
  
### TreeSet`<E>` 클래스

데이터가 정렬된 상태로 저장되는 이진 검색 트리(binary search tree)의 형태로 요소를 저장합니다.

## Set 인터페이스 메소드
![](https://github.com/kabommm/TIL/blob/main/Language/img/set.PNG)

## Map 컬렉션 클래스

List와 Set 인터페이스는 모두 Collection 인터페이스를 상속받지만, 구조상의 차이로 인해 Map 인터페이스는 별도로 정의됩니다.

키와 값을 하나의 쌍으로 저장하는 방식(key-value 방식), 중복 키x,  중복 값은 허용

1. HashMap`<K, V>`

2. Hashtable`<K, V>`

3. TreeMap`<K, V>`

## HashMap`<K, V>` 클래스 메소드
![](https://github.com/kabommm/TIL/blob/main/Language/img/HashMap.PNG)

### 메소드 추가

- getOrDefault("A",false)

get을 사용했는데 Key 값이 없으면 오류가 나기 때문에 매번 Key의 유무를 확인해야 하는 번거로움이 있다 하지만 getOrDefault를 사용하면 
A가 있다면 A의 value를반환 A가 없다면 false반환

### Hashtable`<K, V>` 클래스

HashMap 클래스에서 사용할 수 있는 메소드와 거의 같습니다. 하지만 현재에는 기존 코드와의 호환성을 위해서만 남아있으므로, Hashtable 클래스보다는 HashMap 클래스를 사용하는 것이 좋습니다.

### TreeMap`<K, V>` 클래스

키와 값을 한 쌍으로 하는 데이터를 이진 검색 트리(binary search tree)의 형태로 저장합니다.

## TreeMap`<K, V>` 클래스 메소드
![](https://github.com/kabommm/TIL/blob/main/Language/img/TreeMap1.PNG)
![](https://github.com/kabommm/TIL/blob/main/Language/img/TreeMap2.PNG)
![](https://github.com/kabommm/TIL/blob/main/Language/img/TreeMap3.PNG)

## Iterator`<E>` 인터페이스
  
  자바의 컬렉션 프레임워크는 컬렉션에 저장된 요소를 읽어오는 방법을 Iterator 인터페이스로 표준화하고 있습니다.
  
  Collection 인터페이스에서는 Iterator 인터페이스를 구현한 클래스의 인스턴스를 반환하는 iterator() 메소드를 정의하여 각 요소에 접근하도록 하고 있습니다.

 따라서 Collection 인터페이스를 상속받는 List와 Set 인터페이스에서도 iterator() 메소드를 사용할 수 있습니다. 
  
```
  LinkedList<Integer> lnkList = new LinkedList<Integer>();

 

lnkList.add(4);

lnkList.add(2);

lnkList.add(3);

lnkList.add(1);

 

Iterator<Integer> iter = lnkList.iterator();

while (iter.hasNext()) {

    System.out.print(iter.next() + " ");

}
```
## Iterator`<E>` 메소드
![](https://github.com/kabommm/TIL/blob/main/Language/img/Iterator.PNG)

## ListIterator`<E>` 인터페이스

Iterator 인터페이스를 상속받아 여러 기능을 추가한 인터페이스

Iterator 인터페이스는 컬렉션의 요소에 접근할 때 한 방향으로만 이동할 수 있지만
ListIterator 인터페이스는 컬렉션 요소의 대체, 추가 그리고 인덱스 검색 등을 위한 작업에서 양방향으로 이동하는 것을 지원합니다.

단, ListIterator 인터페이스는 List 인터페이스를 구현한 List 컬렉션 클래스에서만 listIterator() 메소드를 통해 사용할 수 있습니다.

## ListIterator`<E>` 메서드
![](https://github.com/kabommm/TIL/blob/main/Language/img/ListIterator.PNG)

## Comparable`<T>` 인터페이스

객체를 정렬하는 데 사용되는 메소드인 compareTo() 메소드를 정의하고 있습니다.

자바에서 같은 타입의 인스턴스를 서로 비교해야만 하는 클래스들은 모두 Comparable 인터페이스를 구현하고 있습니다.

따라서 Boolean을 제외한 래퍼 클래스나 String, Time, Date와 같은 클래스의 인스턴스는 모두 정렬 가능합니다.

이때 기본 정렬 순서는 작은 값에서 큰 값으로 정렬되는 오름차순이 됩니다.

## Comparable`<T>` 메서드
![](https://github.com/kabommm/TIL/blob/main/Language/img/Comparable.PNG)

## Comparator`<T>` 인터페이스

Comparator 인터페이스는 Comparable 인터페이스와 같이 객체를 정렬하는 데 사용되는 인터페이스입니다.

Comparable 인터페이스를 구현한 클래스는 기본적으로 오름차순으로 정렬되는 
반면에 Comparator 인터페이스는 내림차순이나 아니면 다른 기준으로 정렬하고 싶을 때 사용할 수 있습니다.

즉, Comparator 인터페이스를 구현하면 오름차순 이외의 기준으로도 정렬할 수 있게 되는 것입니다.

이때 Comparator 인터페이스를 구현한 클래스에서는 compare() 메소드를 재정의하여 사용하게 됩니다.

## Comparator`<T>` 메서드
![](https://github.com/kabommm/TIL/blob/main/Language/img/Comparator.PNG)

## 참고

<http://www.tcpschool.com/java/java_collectionFramework_concept>

<https://st-lab.tistory.com/142?category=856997>


