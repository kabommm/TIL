# Collect

> Collectors란 "Stream을 일반적인 List, Set등으로 변경시키는 Stream 메서드"

### toList, toSet
- Collectors.toList()
Stream에서 작업한 결과를 List로 반환받을 수 있다. 

이용할 리스트
```
List<String> givenList = Arrays.asList("a", "bb", "cc", "bb");
```

```
List<String> result = givenList.stream().collect(Collectors.toList()); // a, bb, ccc, dd
for (String s : fruitList) {
    System.out.println(s);
}
만약 해당 결과를 set으로 반환받기를 원한다면 Collectors.toSet()을 사용하면 된다.

Set<String> result = givenList.stream().collect(Collectors.toSet()); // a, bb, ccc
for (String s : fruitList) {
    System.out.println(s);
}
```

### toCollection
toCollection 메서드를 이용하면 특정한 Collection으로 implementation이 가능합니다.

아래는 Stream 요소들을 LinkedList로 변환하는 방법입니다.
```
givenList.stream().collect(Collectors.toCollection(LinkedList::new));
```

### toMap
toMap collector는 Stream elements들을 Map instance로 변경하는 메서드입니다. 

keyMapper, valueMapper를 이용하여 처리할 수 있습니다. toMap(keyMapper, valueMapper)의 형태를 띄게 됩니다.
```
Map<String, Integer> result = givenList.stream().collect(toMap("key", String::length);
```
 key라는 이름의 key에 4가지의 elements가 들어가기 때문에 key 충돌이 발생 (key 중복) 따라서 아래와 같이 수정한다.
 ```
 Map<String, Integer> result = givenList.stream()
  .collect(toMap("key", String::length, (old, new) -> old));
 ```
 
### collectingAndThen

Collecting을 진행한 후 그 결과로 메서드를 하나 더 호출 할 수 있게 해줍니다.
```
System.out.println(givenList.stream().collect(collectingAndThen(toList(), Collection::toString)));
```

### Collectors.joining()

Stream 요소를 1개의 String 객체로 변환

```
String result = givenList.stream().collect(joining()); // abbcccdd
```

Collectors.joining()은 총 3개의 인자를 받을 수 있는데, 이를 이용하면 간단하게 String을 조합할 수 있다.

- delimiter : 각 요소 중간에 들어가 요소를 구분시켜주는 구분자
- prefix : 결과 맨 앞에 붙는 문자
- suffix : 결과 맨 뒤에 붙는 문자

```
String listToString = productList.stream()
	.map(Product::getName)
	.collect(Collectors.joining());
// potatoesorangelemonbreadsugar

String listToString = productList.stream()
	.map(Product::getName)
	.collect(Collectors.joining(" "));
// potatoes orange lemon bread sugar

String listToString = productList.stream()
  	.map(Product::getName)
  	.collect(Collectors.joining(", ", "<", ">"));
// <potatoes, orange, lemon, bread, sugar>
```
### counting

elements의 수를 세는 것입니다.
```
Long result = givenList.stream().collect(counting());
```

### Collectors.averagingInt(), Collectors.summingInt(), Collectors.summarizingInt()
Stream에서 작업한 결과의 평균값이나 총합 등을 구함

```
Double averageAmount = productList.stream()
	.collect(Collectors.averagingInt(Product::getAmount));

// 86
Integer summingAmount = productList.stream()
	.collect(Collectors.summingInt(Product::getAmount));

// 86
Integer summingAmount = productList.stream()
    .mapToInt(Product::getAmount)
    .sum();
```
1개의 Stream으로부터 갯수, 합계, 평균, 최댓값, 최솟값을 한번에 얻고 싶은 경우에는 ollectors.summarizingInt()를 이용

이를 이용하면 IntSummaryStatistics 객체가 반환되며, 필요한 값에 대해 get 메소드를 이용하여 원하는 값을 꺼내면 된다.

개수: getCount()
합계: getSum()
평균: getAverage()
최소: getMin()
최대: getMax()
```
IntSummaryStatistics statistics = productList.stream()
    .collect(Collectors.summarizingInt(Product::getAmount));

//IntSummaryStatistics {count=5, sum=86, min=13, average=17.200000, max=23}
```

### Collectors.groupingBy()
Stream에서 작업한 결과를 특정 그룹으로 묶고 결과는 Map으로 반환

groupingBy는 매개변수로 함수형 인터페이스 ![Function]()을 필요로 한다. 같은 수량일 경우에는 List로 묶어서 값을 반환받게 된다.

```
Map<Integer, List<Product>> collectorMapOfLists = productList.stream()
  .collect(Collectors.groupingBy(Product::getAmount));

/*
{23=[Product{amount=23, name='potatoes'}, Product{amount=23, name='bread'}], 
 13=[Product{amount=13, name='lemon'}, Product{amount=13, name='sugar'}], 
 14=[Product{amount=14, name='orange'}]}
 */
 ```
 
### Collectors.partitioningBy()
 함수형 인터페이스 Predicate를 받아 Boolean을 Key값으로 partitioning한다.

```
Map<Boolean, List<Product>> mapPartitioned = productList.stream()
	.collect(Collectors.partitioningBy(p -> p.getAmount() > 15));

/*
{false=[Product{amount=14, name='orange'}, Product{amount=13, name='lemon'}, Product{amount=13, name='sugar'}], 
 true=[Product{amount=23, name='potatoes'}, Product{amount=23, name='bread'}]}
 */
```


## 참고
<https://mangkyu.tistory.com/114>
<https://sabarada.tistory.com/41>
<https://codechacha.com/ko/java8-stream-collect/>
