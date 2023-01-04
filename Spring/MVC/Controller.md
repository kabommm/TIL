# Controller

Controller는 화면에서 넘어오는 매개변수들을 이용해 Service객체를 호출하는 역할

- 컨트롤러 구조
```
@Controller
@RequestMapping("/blog")

public class BlogController {
  @GetMapping({"/", "/list"})
  public String list(){
    return "/blog/list";  //templates/blog/list.html 위치 리턴
    }
}    
```
