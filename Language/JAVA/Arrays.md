# Arrays 클래스

- java.util.Arrays 클래스
Arrays 클래스에는 배열을 다루기 위한 다양한 메소드가 포함되어 있습니다.

Arrays 클래스의 모든 메소드는 클래스 메소드(static method)이므로, 객체를 생성하지 않고도 바로 사용할 수 있습니다.

이 클래스는 java.util 패키지에 포함되므로, 반드시 import 문으로 java.util 패키지를 불러오고 나서 사용해야 합니다.

- java.util 패키지
java.util 패키지에는 프로그램을 개발하는 데 사용할 수 있는 유용한 유틸리티 클래스가 다수 포함되어 있습니다.

실제로 java.lang 패키지 다음으로 가장 많이 사용되는 패키지가 java.util 패키지입니다.

하지만 import 문을 사용하지 않아도 바로 사용할 수 있는 java.lang 패키지와는 달리 java.util 패키지는 import 문으로 패키지를 불러오고 나서야 클래스 이름만으로 사용할 수 있습니다.

## binarySearch() 메소드
binarySearch() 메소드는 전달받은 배열에서 특정 객체의 위치를 이진 검색 알고리즘을 사용하여 검색한 후, 해당 위치를 반환합니다.

이 메소드는 이진 검색 알고리즘을 사용하므로, 매개변수로 전달되는 배열이 sort() 메소드 등을 사용하여 미리 정렬되어 있어야만 제대로 동작합니다.
```
int[] arr = new int[1000];

for(int i = 0; i < arr.length; i++) {

    arr[i] = i;

}

System.out.println(Arrays.binarySearch(arr, 437));  //437
```
## copyOf() 메소드
copyOf() 메소드는 전달받은 배열의 특정 길이만큼을 새로운 배열로 복사하여 반환합니다.

copyOf() 메소드는 첫 번째 매개변수로 원본 배열을 전달받고, 두 번째 매개변수로 원본 배열에서 새로운 배열로 복사할 요소의 개수를 전달받습니다.

그리고 원본 배열과 같은 타입의 복사된 새로운 배열을 반환합니다.

이때 새로운 배열의 길이가 원본 배열보다 길면, 나머지 요소는 배열 요소의 타입에 맞게 다음과 같은 기본값으로 채워집니다.
```
int[] arr1 = {1, 2, 3, 4, 5};

① int[] arr2 = Arrays.copyOf(arr1, 3);

for (int i = 0; i < arr2.length; i++) {
    System.out.print(arr2[i] + " ");  //1 2 3
}

② int[] arr3 = Arrays.copyOf(arr1, 10);

for (int i = 0; i < arr3.length; i++) {
    System.out.print(arr3[i] + " ");  //1 2 3 4 5 0 0 0 0 0 
}
```
## copyOfRange() 메소드

copyOfRange() 메소드는 전달받은 배열의 특정 범위에 해당하는 요소만을 새로운 배열로 복사하여 반환합니다.

copyOfRange() 메소드는 첫 번째 매개변수로 복사의 대상이 될 원본 배열을 전달받습니다.

두 번째 매개변수로는 원본 배열에서 복사할 시작 인덱스를 전달받고, 세 번째 매개변수로는 마지막으로 복사될 배열 요소의 *바로 다음 인덱스*(주의)를 전달받습니다.

즉, 세 번째 매개변수로 전달된 인덱스 바로 전까지의 배열 요소까지만 복사됩니다.

```
int[] arr1 = {1, 2, 3, 4, 5};

 

int[] arr2 = Arrays.copyOfRange(arr1, 2, 4);

for (int i = 0; i < arr2.length; i++) {

    System.out.print(arr2[i] + " ");  //3 4

}
```


## fill() 메소드

fill() 메소드는 전달받은 배열의 모든 요소를 특정 값으로 초기화해 줍니다.

fill() 메소드는 첫 번째 매개변수로 초기화할 배열을 전달받고, 두 번째 매개변수로 초기값을 전달받습니다.

따라서 이 메소드는 전달받은 원본 배열의 값을 변경하게 됩니다.
```
int[] arr = new int[10];

Arrays.fill(arr, 7);

for (int i = 0; i < arr.length; i++) {
    System.out.print(arr[i] + " "); //7 7 7 7 7 7 7 7 7 7 
}
```

## sort() 메소드

sort() 메소드는 전달받은 배열의 모든 요소를 오름차순으로 정렬합니다.

```
int[] arr = {5, 3, 4, 1, 2};

Arrays.sort(arr);

for (int i = 0; i < arr.length; i++) {
    System.out.print(arr[i] + " "); // 1 2 3 4 5
}
```

## asList() 메소드

  - 배열을 ArrayList로 변환해준다.
  - asList로 만들어진 List는 원소 추가(add)불가 및 값 변경 시 원본 배열 값도 변경됨
  - 원소 추가 및 원본 배열 유지를 위해선 new List 사용
  ```
  String[] strArr1 = {"aa", "bb", "cc"};
  List<String> list1 = Arrays.asList(strArr1);

  list1.set(0, "hi");
  list1.add("dd"); // java.lang.UnsupportedOperationException

  System.out.println(Arrays.toString(strArr1)); // [hi, bb, cc]
  System.out.println(list1.toString()); // [hi, bb, cc]


  String[] strArr2 = {"aa", "bb", "cc"};
  List<String> list2 = new ArrayList<String>(Arrays.asList(strArr2));

  list2.set(0, "hi");
  list2.add("dd");

  System.out.println(Arrays.toString(strArr2)); // [aa, bb, cc]
  System.out.println(list2.toString()); // [hi, bb, cc, dd]	
  ```


## equals()와 deepEquals() 메소드

전달받은 두 배열이 같은지를 확인함.

equals는 일차원 배열에만 사용이 가능하고, deepEquals는 다차원 배열에 사용이 가능하다.
```
String [][] arr = new String[][]{ {"A", "B"}, {"a", "b"} };
String [][] arr2 = new String[][]{ {"A", "B"}, {"a", "b"} };

Arrays.equals(arr, arr2); //false - 다차원 배열에 equals를 사용하면, 배열에 저장된 내용이 같더라도, equals는 주솟값을 비교하기 때문에 false를 반환한다.
Arrays.deepEquals(arr, arr2); //true
```

## toString(), deepToString() 메소드
  - 배열 element 출력
  - 1차원 배열일 경우 toString 사용, 다차원 배열일 경우 deepToString 사용
  ```
  int[] intStr1 = {1, 2, 3};
  System.out.println(Arrays.toString(intStr1)); // [1, 2, 3]
  ```

## 참고
<http://www.tcpschool.com/java/java_api_arrays>
<https://mi2mic.tistory.com/189>
<https://ttl-blog.tistory.com/178>
