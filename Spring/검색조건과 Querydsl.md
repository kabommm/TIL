# Querydsl
- 쿼리 메소드와 @Query를 사용하는 기능은 선언할 때 고정된 형태의 값을 가진다는 단점이 있습니다. 
- 이 때문에 복잡한 조합을 잉요하는 경우에서는 동적으로 쿼리를 생성해서 처리할 수 있는 기능이 필요한데 이를 처리할 수 있는 기술이 바로 Querydsl
- 복잡한 검색조건이나 조인, 서브 쿼리 등의 기능도 구현 가능
- 엔티티 클래스를 Q도메인 클래스로 변환하는 방식을 이용하기 때문에 추가 설정이 필요

  - build.gradle에 설정 추가

  ```
  buildscript { ext { queryDslVersion = "5.0.0" } } // 1. 맨 위에 queryDsl version 정보 추가
  id 'com.ewerk.gradle.plugins.querydsl' version '1.0.10' //2. plugins { ... }에 추가
  implementation "com.querydsl:querydsl-jpa:${queryDslVersion}"
	implementation "com.querydsl:querydsl-apt:${queryDslVersion}" //3. dependencies { ...}에 추가
  
  //4. 맨 아래 queryDSL 설정 추가
  
  // querydsl에서 사용할 경로 설정
  def querydslDir = "$buildDir/generated/querydsl"
  // JPA 사용 여부와 사용할 경로를 설정
  querydsl {
    jpa = true
    querydslSourcesDir = querydslDir
  }
  sourceSets {
    main.java.srcDir querydslDir
  }
  compileQuerydsl{
    options.annotationProcessorPath = configurations.querydsl
  }
  configurations {
    compileOnly {
      extendsFrom annotationProcessor
    }
    querydsl.extendsFrom compileClasspath
  }
  ```
- 위의 설정을 마치고 나면 build 폴더 안에 엔티티클래스가 Q도메인 클래스로 변환된 것을 확인 
- Repository에 설정 추가
Querydsl을 이용하면 Repository에 QuerydslPredicateExecutor라는 인터페이스를 추가로 상속
```
public interface GuestbookRepository extends JpaRepository<Guestbook, Long>, QuerydslPredicateExecutor<Guestbook> {
}
```

- Querydsl 사용법
  - BooleanBuilder 생성
  - 조건에 맞는 구문은 Querydsl에서 사용하는 Predicate 타입의 함수를 생성합니다.
  - BooleanBuilder에 작성된 Predicate를 추가하고 실행합니다.
  ```
  @Test   //단일 항목 검색
    public void testQuery(){
        Pageable pageable = PageRequest.of(0, 10, Sort.by("gno").descending());
        QGuestbook qGuestbook = QGuestbook.guestbook; //Q도메인 클래스를 얻어옴, 그러면 엔티티 클래스의 title같은 필드를 변수로 사용가능

        String keyword = "1";   //제목에 1이라는 글자가 있는 엔티티 검색

        BooleanBuilder builder = new BooleanBuilder(); //BooleanBuilder는 where문에 들어가는 조건들을 넣어주는 컨테이너

        BooleanExpression expression = qGuestbook.title.contains(keyword); //필드값과 원하는 조건을 결합해 생성

        builder.and(expression); //만들어진 조건을 where문에 and나 or같은 키워드와 결합

        //BooleanBuilder는 게스트북레포에 추가된 QuerydslPredicateExecutor 인터페이스의 findAll()을 사용가능
        Page<Guestbook> result = guestbookRepository.findAll(builder, pageable);

        result.stream().forEach(guestbook -> {
            System.out.println(guestbook);
        });
    }
  ```
  ```
   @Test   //다중 항목 검색 = 복합 조건
    public void testQuery2(){
        Pageable pageable = PageRequest.of(0, 10, Sort.by("gno").descending());
        QGuestbook qGuestbook = QGuestbook.guestbook;
        String keyword = "1";   //제목에 1이라는 글자가 있는 엔티티 검색

        BooleanBuilder builder = new BooleanBuilder();

        BooleanExpression exTitle = qGuestbook.title.contains(keyword);

        BooleanExpression exContent = qGuestbook.content.contains(keyword);

        BooleanExpression exAll = exTitle.or(exContent);

        builder.and(exAll); //제목 또는 내용이 있다

        builder.and(qGuestbook.gno.gt(0L)); //gno가 0보다 크다


        Page<Guestbook> result = guestbookRepository.findAll(builder, pageable);

        result.stream().forEach(guestbook -> {
            System.out.println(guestbook);
        });
    }
  ```
