# 순서 알고리즘

```
    public static void main(String[] args) {
        int[] answer = {100, 90, 80, 70, 60};
        int[] rank = {1, 1, 1, 1, 1};
        
        for(int i=0; i < answer.length; i++){
            rank[i] =1;   //for문이 한바퀴 돌 때마다 1로 초기화
            for(int j=0; j < answer.length; j++){ //인덱스 비교
                if(answer[i] < answer[j]){  //i인덱스 값보다 크면 순위 증가
                    rank[i] = rank[i] +1;
                }
            }
        }    
        for(int i =0; i<answer.length; i++){    //점수에따른 순위 출력
          System.out.pringln("점수: " + answer[i] + "순위: " + rank[i] );
        }
    }
```
