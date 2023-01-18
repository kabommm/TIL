# 재귀 기초- 팩토리얼

```
public static void main(String[] args) {
        int n = 5;
        System.out.println(n +"! = " + factorial(n)); 
    }
    static int factorial(int n) {
        if (n == 1) {
            return 1;
        }else{
          return n * factorial(n - 1);
        }
        
 
    }

```

## 참고
<https://codewos.tistory.com/22>
