# JPA

> Java Persistence API - Java 언어를 통해서 데이터베이스와 같은 영속 계층을 처리하고자 하는 스펙

![](https://github.com/kabommm/TIL/blob/main/Spring/img/JPA.PNG)

## ORM

- ORM(Object Relational Mapping)은 객체지향 패러다임을 관계형 데이터베이스에 보존하는 기술
- ORM을 이용해 SQL Query가 아닌 직관적인 코드로 데이터 조작할 수 있음, 쿼리문이 복합해지면 ORM표현으로 한계가 있으므로 JPQL, QueryDSL 등을 사용
- 객체지향 구조와 관계형 DB 구조는 유사함

      객체지향 구조의 'class', 클래스 멤버 변수를 타입을 포함해 선언 <대응> 관계형 DB의 '테이블', 컬럼을 정의하고 컬럼에 맞는 데이터 타입을 지정
      객체지향 구조의 '인스턴스', <대응> 관계형 DB의 'Row'
      객체지향 구조의 '레퍼런스' <대응> 관계형 DB의 '관계'

  > 이러한 특징을 기초해 객체지향을 자동으로 관계형 DB에 맞게 처리해주는 기법이 ORM의 시작

## Hibernate

- JPA의 구현체 중 하나로 '오픈소스'로 ORM을 지원하는 프레임워크
- 다른 프레임워크도 그러하지만, Hibernate는 단독으로 프로젝트에 적용이 가능한 독립된 프레임워크

## JPA를 사용해야 하는 이유

- sql 중심적인 개발에서 객체 중심적인 개발이 가능

- 생산성 증가

- 유지보수 용이
  엔티티 필드가 되는 객체를 다뤄서 데이터베이스를 동작시키기 때문에 유지보수가 더욱 간결하다.

- 객체와 RDB간의 패러다임 불일치 해결

## JPA의 영속성

- 영속성 - 데이터를 생성한 프로그램이 종료되어도 사라지지 않는 데이터의 특성

Spring Data Jpa를 사용하면 기본으로 엔티티 매니저가 활성화되어있어 트랜잭션(@Transactional) 안에서 DB에서 데이터를 가져오면 이 데이터는 영속성 컨텍스트가 유지된 상태이다.
이 상태에서 해당 데이터 값을 변경하면 트랜잭션이 끝나는 시적에 해당 테이블에 변경 내용을 반영하게 된다.

- Entity Class - 자바 클래스에 @Entity 어노테이션을 붙여, 테이블과 매핑한다고 JPA에게 알려주는 클래스다.
  엔티티 클래스에서 만들어진 객체를 엔티티라고 한다.

## JpaRepository

- JpaRepository - Spring Data JPA에서 제공하는 인터페이스로 설계하는데 스프링 내부에서 자동으로 객체를 생성하고 실행하는 구조

```
public interface MemoRepository extends JpaRepository<Memo, Long> {
}
```

- JpaRepository를 사용할 때는 엔티티의 타입 정보(Memo 클래스 타입)와 @Id의 타입을 지정

  ![](https://github.com/kabommm/TIL/blob/main/Spring/img/JpaRepository.PNG)

- JpaRepository가 활용하는 CRUD 메서드

  - insert 작업: save(엔티티 객체)
  - select 작업: findById(키 타입), getOne(키 타입)
  - update 작업: save(엔티티 객체)
  - delete 작업: deleteById(키 타입), dlelete(엔티티 객체)

  - 등록

  ```
    @Test
    public void testInsertDummies(){
        IntStream.rangeClosed(1,100).forEach(i -> {
            Memo memo = Memo.builder().memoText("Sample..."+i).build(); //MemoText는 Not Null이므로 반드시 데이터를 넣어줌
            memoRepository.save(memo);
        });
    }
  ```

  - 조회

  ```
    @Test
        public void testSelect(){

            Long mno = 100L;    //DB에 존재하는 mno
            //findById()는 Optional 타입으로 반환되기 때문에 한번 더 결과가 존재하는지를 체크하는 형태로 작성
            Optional<Memo> result = memoRepository.findById(mno);

            System.out.println("----------------------");

            if(result.isPresent()){
                Memo memo = result.get();
                System.out.println(memo);
            }
        }

        @Test
        @Transactional
        public void testSelect2(){

            Long mno = 100L;    //DB에 존재하는 mno
        //getOne()은 트랜잭션 어노테이션이 필요, 실제 객체가 필요한 순간까지 SQL을 실행하지 않는다.
            Memo memo = memoRepository.getOne(mno);

            System.out.println("----------------------");

            System.out.println(memo);
        }
  ```

  - 수정

  ```
      @Test
          public void testUpdate(){   //100번의 Memo객체의 memoText를 업데이트로 변경
                  Memo memo = Memo.builder().mno(100L).memoText("업데이트").build();
                  System.out.println(memoRepository.save(memo));

          }
  ```

  - 삭제

  ```
      @Test
      public void testDelete(){
          Long mno = 100L;    //DB에 존재하는 mno
          memoRepository.deleteById(mno);

      }
  ```

### 출처

- <https://velog.io/@modsiw/JPAJava-Persistence-API%EC%9D%98-%EA%B0%9C%EB%85%90>
- <https://velog.io/@hermaeus/7.JpaRepository-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4>
