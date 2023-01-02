# 페이징/정렬 처리

- 페이징 처리와 정렬은 findAll()이라는 메서드를 사용한다.
- findAll()은 PagingANdSortRepository의 메서드로 파라미터로 전달되는 Pageable이라는 타입의 객체에 의해서 실행되는 쿼리를 결정하게 된다.

## 페이징 처리

- PageRequest 생성자를 보면 page, size, Sort라는 정보를 이용해서 객체를 생성, 객체를 생성하기 위해서는 static 메서드인 of()를 이용해서 처리
  - of(int page, int size): 0부터 시작하는 페이지 번호와 개수(size), 정렬이 지정되지 않음
  - of(int page, int size, Sort.Direction direction, String...props): 0부터 시작하는 페이지 번호와 개수, 정렬의 방향과 정렬 기준 필드들
  - of(int page, int size, Sort sort): 페이지 번호와 개수, 정렬 관련 정보

```
@Test
    public void testPageDefault(){
        //1페이지 10개
        Pageable pageable = PageRequest.of(0,10);

        Page<Memo> result = memoRepository.findAll(pageable);

        System.out.println(result);

        System.out.println("----------------------");
        //다음은 Page<엔티티 타입>의 여러 메서드
        System.out.println("전체 페이지: " + result.getTotalPages());    //총 몇 페이지
        System.out.println("전체 개수: " + result.getTotalElements());    //전체 개수
        System.out.println("페이지 번호: " + result.getNumber());    //현재 페이지 번호 0부터 시작
        System.out.println("페이지당 데이터 수: " + result.getSize());    //페이지당 데이터 개수
        System.out.println("다음 페이지 존재?: " + result.hasNext());    //다음 페이지
        System.out.println("시작 페이지 존재?: " + result.isFirst());    //시작 페이지(0) 여부

        for (Memo memo : result.getContent()){  //getContent()는 List<엔티티 타입>으로 처리
            System.out.println(memo);
        }


    }
```

## 정렬 조건

```
@Test
    public void testSort(){
        Sort sort1 = Sort.by("mno").descending();
        Sort sort2 = Sort.by("memoText").ascending();
        Sort sortAll = sort1.and(sort2);

        Pageable pageable = PageRequest.of(0, 10, sortAll);

        Page<Memo> result = memoRepository.findAll(pageable);

        result.get().forEach(memo -> {  //get()는 Stream<엔티티 타입>으로 반환8
            System.out.println(memo);
        });


    }
```
