# Annotation

```
@Entity
@Table(name = "tbl_memo")
@ToString
@Getter
@Builder
@AllArgsConstructor
@NoArgsConstructor
public class Memo {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long mno;

    @Column(length = 200, nullable = false)
    private String memoText;
}
```

- ### @Entity
  해당 클래스가 엔티티를 위한 클래스이며, 해당 클래스의 인스턴스들이 JPA로 관리되는 엔티티 객체라는 것을 의미
- ### @Table
  @DB에서 엔티티 클래스를 어떠한 테이블로 생성할 것인지에 대한 정보를 담기 위한 어노테이션

테이블 이름뿐만 아니라 인덱스 등을 생성하는 설정도 가능하다.
name속성값이 없는 경우에는 클래스의 이름과 동일한 이름으로 테이블 생성

- ### @Id & @GeneratedValue
  @Entity가 붙은 클래스는 PK에 해당하는 특정 필드를 @Id로 지정해야만 한다.

@Id가 사용자가 입력하는 값을 사용하는 경우가 아니면 자동으로 생성되는 번호를 사용하기 위해 @GeneratedValue라는 어노테이션을 활용한다.

(strategy = GenerationType.IDENTITY)는 PK를 자동으로 생성하고자 할 때 사용한다.(키 생성 전략)

키 생성 전략은 크게 다음과 같습니다.

- AUTO(default) - JPA 구현체가 생성 방식을 결정
- IDENTITY - 사용하는 DB가 키 생성을 결정, MySQL이나 MariaDB의 경우 auto increment(새로운 레코드가 기록될 때 마다 다른 번호를 가짐)방식을 이용
- SEQUENCE - DB의 sequence를 이용해서 키를 생성. @SequenceGenerataor와 같이 사용
- TABLE - 키 생성 전용 테이블을 생성해서 키 생성. @TableGeneretor와 같이 사용

- ### @Column

  필드의 속성을 지정할 수 있음

- ### @Getter

- ### @Builder
  객체를 생성할 수 있게 처리

@Builder를 이용하기 위해서는 @AllArgsConstructor와 @NoArgsConstructor를 항상 같이 처리해야 컴파일 에러가 발생하지 않는다.

- ### @AllArgsConstructor

- ### @NoArgsConstructor

- ### @Commit
  최종 결과를 커밋하기 위해서 사용

이를 적용하지 않으면 롤백이 발생해 결과가 반영되지 않는다.

- ### @Transactional
