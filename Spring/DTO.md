# DTO

- DTO는 엔티티 객체와 달리 각 계층끼리 주고받는 우편물이나 상자의 개념입니다.

- 엔티티와 유사한 점: 순수하게 데이터를 담고 있다.

- 엔티티와 다른 점: 목적 자체가 데이터의 전달이므로 읽고, 쓰는 것이 모두 허용되고 일회성으로 사용되는 성격이 강하다.
그렇기 때문에 엔티티와 DTO는 분리해서 처리한다.

- DTO는 엔티티와 거의 동일한 필드들을 가지고 getter/setter를 통해 자유롭게 값을 변경할 수 있게 구성합니다.
- DTO -> Entity 변환

  JPA로 처리하기 위해서는 반드시 엔티티 타입의 객체로 변환해야 한다.
  - Service 인터페이스
  ```
  public interface GuestbookService {
  Long register(GuestbookDTO dto);

  PageResultDTO<GuestbookDTO, Guestbook> getList(PageRequestDTO requestDTO);

  //default를 이용하면 기존에 추상 클래스를 통해 전달해야하는 실제 코드를 인터페이스에 선언 가능
  default Guestbook dtoToEntity(GuestbookDTO dto){
      Guestbook entity = Guestbook.builder()
              .gno(dto.getGno())
              .title(dto.getTitle())
              .content(dto.getContent())
              .writer(dto.getWriter())
              .build();
      return entity;
      }
      default GuestbookDTO entityToDto(Guestbook entity){
          GuestbookDTO dto = GuestbookDTO.builder()
                  .gno(entity.getGno())
                  .title(entity.getTitle())
                  .content(entity.getContent())
                  .writer(entity.getWriter())
                  .regDate(entity.getRegDate())
                  .modDate(entity.getModDate())
                  .build();
          return dto;
      }
  }
  ```
  Service 인터페이스에서 default 메서드를 사용하면 추상 클래스를 통하지 않고 구현 클레스에서 구현이 가능하다.
  
  - ServiceTests(실제로는 Controller에 적용)
  ```
  public class GuestServiceTests {
    @Autowired
    private GuestbookService service;

    @Test
    public void testRegister(){
        GuestbookDTO guestbookDTO = GuestbookDTO.builder()
                .title("Sample Title...")
                .content("Sample Content...")
                .writer("user0")
                .build();

        System.out.println(service.register(guestbookDTO));
    }
  ```
  새 게시물이 dtoToEntity가 적용된 형태로 등록 
  
  - ServiceImpl 클래스
  ```
  @Service
  @Log4j2
  @RequiredArgsConstructor    //의존성 자동 주입
  public class GuestbookServiceImpl implements GuestbookService {
      private final GuestbookRepository repository; //반드시 final로 선언
  @Override
      public Long register(GuestbookDTO dto){
      log.info("DTO----------------------");
      log.info(dto);

      Guestbook entity = dtoToEntity(dto);
      log.info(entity);

      repository.save(entity);
      return entity.getGno();
    }
  }
  ```
