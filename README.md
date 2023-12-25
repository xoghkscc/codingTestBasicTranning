# codingTest

## 1일차

### 1번 문제
<img width="773" alt="image" src="https://github.com/xoghkscc/codingTest/assets/82793713/82799151-b936-460d-a2ce-527fa656881a">

```
class Solution {
    public int[] solution(int[] num_list, int n) {
        int[] answer = new int[num_list.length-(n-1)];
        int index = 0;
        for(int i = n-1; i < num_list.length; i++){
            answer[index++] = num_list[i];
        }
        
        return answer;
    }
}
```
