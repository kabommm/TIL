# 삽입 정렬

- 시간 복잡도: O(n^2)

- 공간 복잡도: O(1)

현재 비교하고자 하는 target(타겟)과 그 이전의 원소들과 비교하며 자리를 교환(swap)하는 정렬 방법

데이터를 '비교'하면서 찾기 때문에 '비교 정렬'이며 정렬의 대상이 되는 데이터 외에 추가적인 공간을 필요로 하지 않기 때문에 '제자리 정렬(in-place sort)'이기도 하다.

선택 정렬과는 달리 삽입 정렬은 '안정 정렬'이다.

- 과정(오름차순 기준)

1. 현재 타겟이 되는 숫자와 이전 위치에 있는 원소들을 비교한다. (첫 번째 타겟은 두 번째 원소부터 시작한다.

2. 타겟이 되는 숫자가 이전 위치에 있던 원소보다 작다면 위치를 서로 교환한다.

3. 그 다음 타겟을 찾아 위와 같은 방법으로 반복한다. 

![]()

- 삽입 정렬 구현

![]()

- 시간 복잡도 유도

최선의 경우는 O(N)이고 최악의 경우를 보자.

N이 정렬해야하는 리스트의 자료 수, i가 타겟이 되는 인덱스라고 할 때 loop(반복문)을 생각해보자.

i=1  일 때, 데이터 비교 횟수는 N-1 번

i=2 일 때, 데이터 비교 횟수는 N-2 번

i=3 일 때, 데이터 비교 횟수는 N-3 번

                   ⋮

i=N-1 일 때, 데이터 비교 횟수는 1 번

-> 1부터 N-1까지 전체의 합 공식N(N-1)/2에서 (N^2 -N) <= (N^2)이므로 -N제외 그리고 상수 2/1 생략 -> N^2

버블 정렬(Bubble Sort)과 이론상 같은 시간복잡도를 갖음에도 비교 수행이 상대적으로 적기 때문에 조금 더 빠르긴 하나 그럼에도 좋은 알고리즘인 것은 아니다.

## 참고

<https://st-lab.tistory.com/179>
