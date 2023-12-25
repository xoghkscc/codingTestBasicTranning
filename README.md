# codingTest

## 1일차

### 1번 문제
<img width="773" alt="image" src="https://github.com/xoghkscc/codingTest/assets/82793713/82799151-b936-460d-a2ce-527fa656881a">

```java
class Solution {
    public int[] solution(int[] num_list, int n) {
        int[] answer = new int[num_list.length-(n-1)]; // num_list의 n번째 원소부터 마지막 원소까지의 개수에 대한 배열 길이를 생성
        int index = 0;
        for(int i = n-1; i < num_list.length; i++){
            answer[index++] = num_list[i];
        }       
        return answer;
    }
}
```

### 2번 문제
<img width="761" alt="image" src="https://github.com/xoghkscc/codingTest/assets/82793713/61d478ec-d927-47a0-a49e-496eb6b0b09e">

```java
class Solution {
    public int[] solution(int[] num_list, int n) {
        int[] answer = new int[num_list.length];
        
        int[] front = new int[n]; -- num_list의 0번째부터 n번째까지 담을 배열
        int[] back = new int[num_list.length - n]; -- num_list의 n+1번째부터 끝까지 담을 배열****
        
        for(int i = 0; i < n; i ++){
            front[i] = num_list[i];
        }
        
        for(int i = 0; i < num_list.length - n; i ++){
            back[i] = num_list[n+i];
        }
        
        int index = 0;
        
        for(int i = 0; i < back.length; i ++){
            answer[index++] = back[i];
        }
        
        for(int i = 0; i < front.length; i ++){
            answer[index++] = front[i];
        }
        
        return answer;
    }
}
```
