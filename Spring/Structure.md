# 프로젝트 구조

- 1. 와이어프레임(화면 설계서)을 제작하고 화면의 URI와 전달되는 파라미터 등을 미리 결정
- 2. 각 화면별로 기능 정리
![](https://github.com/kabommm/TIL/blob/main/Spring/img/ex.PNG)
예시
- 3. 위를 토대로 DB 설계에 필요한 칼럼들을 파악, 관계를 파악하고 ERD 설계

## 스프링 프로젝트 기본 구조
![](https://github.com/kabommm/TIL/blob/main/Spring/img/structure.PNG)
- 브라우저에서 들어오는 Request는 GuestbookController라는 객체로 처리합니다.
- GuestbookRepository는 Spring Data JPA를 이용해서 구성하고, GuestbookServiceImpl 클래스에 주입해서 사용합니다.

DTO와 엔티티 객체의 역할
![](https://github.com/kabommm/TIL/blob/main/Spring/img/DTO.PNG)
- GuestbookRepository는 엔티티 타입을 이용하므로 Service 계층에서는 DTO오 엔티티의 변환을 처리합니다.

# 프로젝트 실행
- 1. 컨트롤러/화면 준비
- 2. 자동으로 처리되는 날짜/시간 설정(엔티티 클래스 생성)
엔티티 작업을 하다 보면, 데이터의 등록 시간과 수정 시간과 같이 자동으로 추가되고 변경되어야 하는 칼럼들이 있습니다.

이를 자동으로 처리할 수 있도록 어노테이션을 이용해서 설정합니다.
- 추가 엔티티 관련 설명
  - JPA 방식에서 엔티티 객체는 유지되고 필요할 때 꺼내서 재사용하는 방식이므로 엔티티 객체에는 어떤 변화가 일어나는 것을 감지하는 리스너가 있다.
  - 엔티티 객체가 생성/변경되는 것을 감지하는 역할은 AuditingEntityListener로 이루어진다.
  - AuditingEntityListener를 활성화 시키려면 Application 클래스에 @EnableJpaAuditing 추가
  ```
  @MappedSuperclass   //테이블이 생성되지 않음, 실제 테이블은 이 클래스를 상속한 엔티티 클래스로 생성
  @EntityListeners(value = {AuditingEntityListener.class})    //AuditingEntityListener가 엔티티 객체 생성/변경을 감지
  //이를 통해 regDate, modDate에 적절한 값 지정
  @Getter
  abstract class BaseEntity {
      @CreatedDate    //JPA에서 엔티티의 생성 시간을 처리
      @Column(name = "regdate", updatable = false)    //updatable = false로 설정하여 regdate 칼럼값은 변경x
      private LocalDateTime regDate;

      @LastModifiedDate   //최종 수정 시간을 자동으로 처리
      @Column(name ="moddate")
      private LocalDateTime modDate;
  }
  ```
- 3. 위에서 작성한 엔티티를 상속받는 또는 그냥 엔티티 클래스를(2번 없는 경우) 생성
- 4. Repository 인페이스 생성
JpaRepository를 상속받는 인터페이스로 구성
- 5. ![DTO](https://github.com/kabommm/TIL/blob/main/Spring/DTO.md)

- 6. Service 계층
서비스 계증에서는 DTO를 이용해서 필요한 내용을 전달받고, 반환하도록 처리하는데 Service인터페이스와 ServiceImpl 클래스를 작성합니다.
- Service interface와 ServiceImpl class 구조를 사용하는 이유?
  - 인터페이스와 구현체를 분리함으로써 구현체를 독립적으로 확장할 수 있으며, 구현체 클래스를 변경하거나 확장해도 이를 사용하는 클라이언트의 코드에 영향을 주지 않도록 하기 위함입니다. 이 같은 추상화를 통한 구현 방식은 객체지향의 특징 중 하나인 다형성과 객체지향의 다섯 가지 원칙 중 하나인 OCP 원칙을 가장 잘 실현해주는 설계 방식
  - OCP(Open Closed Principle): 개방, 폐쇄 원칙이라고 하며 '소프트웨어 개체(클래스, 모듈, 함수 등)는 확장에 대해 열려 있어야 하고, 수정에 대해서는 닫혀 있어야 한다.'는 프로그래밍 원칙
  - 추상화를 통한 구현 방식의 단점: 코드 구조가 복잡해지고, 복잡해진 구조 만큼 코드를 분석하고 확인하는 과정에서 인터페이스를 거쳐 구현체들을 확인해야 하는 번거로움이 생길 수 있습니다.
  - 예시 코드
  
  service 인터페이스
  ```
  public interface MainService {
    ResponseEntity<?> doAction();
  }
  ```
  MainService의 doAction 기능을 구현하는 MainServiceImpl
  ```
  @Service
  public class MainServiceImplA implements MainService {
    @Override
    public ResponseEntity<?> doAction() {
        System.out.println("do Action A");
    }
  }
  ```
  MainService의 doAction 기능을 구현하는 MainServiceImplB
  ```
  @Service
  public class MainServiceImplB implements MainService {
      @Override
      public ResponseEntity<?> doAction() {
          System.out.println("do Action B");
      }
  }
  ```
  - 이러한 구조로 프로젝트를 설계했을 때, interface에서 정의한 기능을 새로운 방식으로 구현해야 한다면 사용해야하는 곳에서 구현체만 손쉽게 바꿀 수 있기 때문에 Service를 인터페이스로 만들고, 해당 기능을 ServiceImpl 라는 class로 구현하는 것입니다.

### 출처

- <https://velog.io/@hermaeus/14.%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EA%B5%AC%EC%A1%B0-%EB%A7%8C%EB%93%A4%EA%B8%B0>
- <https://wildeveloperetrain.tistory.com/49>
