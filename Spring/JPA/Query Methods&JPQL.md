# 쿼리 메서드

- 메서드의 이름 자체가 쿼리의 구문으로 처리되는 기능
  주로 findBy나 getBy로 시작하고 이후에 필요한 필드 조건이나 And, Or와 같은 키워드를 이용해서 메서드의 이름 자체로 질의 조건을 만든다.
- 메서드는 인터페이스에 추가
  - select를 하는 작업이라면 List 타입이나 배열을 이용할 수 있다.
  - 파라미터에 Pageable 타입을 넣는 경우에는 무조건 Page<E>타입
- 쿼리 메서드와 Pageable의 결합

  - 정렬의 관한 부분을 Pageable로 처리해서 메서드를 간략화 할 수 있다.

  ```
  public void testQueryMethodWithPageable(){
      Pageable pageable = PageRequest.of(0, 10, Sort.by("mno").descending());

      Page<Memo> result = memoRepository.findByMnoBetween(10L, 50L, pageable);

      result.get().forEach(memo -> System.out.println(memo));
  }
  ```

  - Pageable을 사용하지 않으면 위와같은 정렬조건이 붙은 findByMnoBetween 메서드는 findAllByMnoBetweenOrderByMnoDesc와 같이 복잡해진다.

# @Query

- 쿼리 메서드는 복잡한 조건을 처리해야 하는 경우에는 불편하므로 간단한 처리만 쿼리 메서드를 이용하고 대부분 @Query를 이용한다.

- @Query의 value는 JPQL(Java Persistence Query Language)로 작성하는데 흔히 '객체지향 쿼리'라고 불리는 구문들이다.

객체지향 쿼리는 테이블 대신 엔티티 클래스를 칼럼 대신에 클래스에 선언된 필드를 이용해서 작성한다.(JPQL과 SQL의 유사성)

- @Query를 이용해서는 다음과 같은 작업을 실행할 수 있습니다.
  - 필요한 데이터만 선별적으로 추출하는 기능이 가능
  - DB에 맞는 순수한 SQL(Native SQL)을 사용하는 기능
  - insert, update, delete와 같은 select가 아닌 DML 등을 처리하는 기능(@Modifying과 함께 사용)
- Query의 파라미터 바인딩
  - where 구문과 그에 맞는 파라미터들을 처리할 때 다음과 같은 방식을 사용한다.
    - ?1, ?2와 1부터 시작하는 파라미터의 순서를 이용하는 방식
    - ':파라미터 이름'을 활용하는 방식
    ```
    @Transactional
    @Modifying
    @Query("update Memo m set m.memoText = :memoText where m.mno = :mno")
    int updateMemoText(@Param("mno") Long mno, @Param("memoText") String memoText );
    ```
- Query와 페이징 처리
  - 쿼리 메서드와 마찬가지로 Pageable 타입의 파라미터를 적용하면 페이징 처리와 정렬에 대한 부분을 작성하지 않을 수 있습니다.
  - 별도의 countQuery라는 속성을 적용해 주고 Pageable 타입의 파라미터를 전달하면 됩니다.
  ```
  @Query(value = "select m from Memo m where m.mno > :mno",
          countQuery = "select count(m) from Memo m where m.mno > :mno" )
  Page<Memo> getListWithQuery(Long mno, Pageable pageable);
  ```
- Object[] 리턴
  - 현재 필요한 데이터만을 Object[]의 형태로 선별적으로 추출할 수 있다.
  - mno, memoText, 현재 시간을 얻어오려 할 때 Memo 엔티티 클래스에는 시간 관련 부분이 없기 때문에 추가 구문이 필요한데 JPQL의 구문을 통해서 구할 수 있다.
  ```
  @Query(value = "select m.mno, m.memoText, CURRENT_DATE from Memo m where m.mno > :mno,
         countQuery = "select count(m) from Memo m where m.mno > :mno" )
  Page<Object[]> getListWithQuery(Long mno, Pageable pageable);
  ```
- Native SQL 처리
  - 경우에 따라서 복잡한 JOIN 구문 등을 처리하기 위해서 어쩔 수 없이 고유의 SQL 구문을 그대로 활용하는 방법
  ```
   @Query(value = "select * from memo where mno > 0", nativeQuery = true)
  List<Object[]> getNativeResult();
  ```
