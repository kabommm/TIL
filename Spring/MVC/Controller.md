# Controller

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
