# codingTest

## 15일자

### 1번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/d46cf7de-3fe5-4a17-b20d-eabddaaaba33)
```java
class Solution {
    public int[] solution(int[] arr) {
        int[] answer = new int[arr.length];
        
        for(int i = 0; i < arr.length; i++){
            if(arr[i] >= 50 && arr[i] % 2 == 0) {
                arr[i] = arr[i] / 2;
            } else if(arr[i] < 50 && arr[i] % 2 == 1){
                arr[i] = arr[i] * 2;
            }
        }   
        answer = arr;    
        return answer;
    }
}
```


### 2번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/31e0ebd7-318f-4a30-836f-bc553c033d86)

```java
import java.util.Arrays; //꼭 기억하자!!
class Solution {
    public int solution(int[] arr) {
        int answer = 0;
        
        int x = 0;
        
        while(true){
            x++;
            
            int[] temp = Arrays.copyOfRange(arr, 0, arr.length); // 단순히 =로 대입하면 주소복사가 되므로 arr 갑이 변경될때 tmp도 같이 변경된다.
            
            for(int i = 0; i < arr.length; i++){
                if(arr[i] >= 50 && arr[i] % 2 == 0) {
                    arr[i] = arr[i] / 2;
                } else if(arr[i] < 50 && arr[i] % 2 == 1){
                    arr[i] = (arr[i] * 2) + 1;
                }

            }  
                       
            if(Arrays.equals(temp, arr)){ // 배열 비교는 Arrays의 equals 메서드를 쓰는 것이 좋다
                answer = x-1;
                break;
            } 
        }
        
         
        return answer;
    }
}
```

*    문제를 이해하기 너무 어려웠으며 Arrays 컬렉션들을 활용해야 문제 풀기가 쉬운 것 같다.



### 3번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/682e8404-3a4c-4edf-b2a5-fbe51130e93c)

```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
        
        for(int i = 0; i < num_list.length; i++){
            while(true){
                if(num_list[i] == 1) break;

                num_list[i] = num_list[i] % 2 == 0 ? num_list[i] / 2 : (num_list[i] - 1) / 2;
                
                answer++;
            
            }
        }     
        return answer;
    }
}
```

### 4번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/7c1293db-b5a1-4d88-956b-a0fc95816777)

```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
        
        if(num_list.length >= 11){
            for(int i = 0; i < num_list.length; i++){
                answer += num_list[i];
            }
        } else {
            answer = 1;
            for(int i = 0; i < num_list.length; i++){
                answer *= num_list[i];
            }
        }
        
        return answer;
    }
}
```

## 14일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/00e40d4a-fcce-45ad-8a37-6ed7fd7ee0eb)

```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
        
        int odd_number = 0; //홀수 합
        int even_number = 0; //짝수 합

        
        for(int i = 0; i < num_list.length; i++){
            if((i+1) % 2 != 0){
                odd_number += num_list[i];
            } else {
                even_number += num_list[i];
            }
        }
        
        answer = odd_number > even_number ? odd_number : even_number;
        
        return answer;
    }
}
```


### 2번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/a601e31b-d551-4f9b-8366-3563e1c4d1ff)

```java
class Solution {
    public String[] solution(String[] names) {
        int length = ((names.length - 1) / 5) + 1; // 첫번째 인원은 무조건 탑승하니까 1을 뺀 나머지 인원들에 대해서 5를 나눈 몫 + 1이 길이이다.
        String[] answer = new String[length];
        
        for(int i = 0; i < length; i++){
            answer[i] = names[i*5];
        }
        
        return answer;
    }
}
```

### 3번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/22dac23c-d434-4310-b63e-65c293eb7e9d)

```java
class Solution {
    public String[] solution(String[] todo_list, boolean[] finished) {
        int todo_count=0; // 해야할 일의 개수
        
        for(int i = 0; i < finished.length; i++){
            if(!finished[i]) todo_count++;
        }
        
        String[] answer = new String[todo_count];
        
        int index=0;
        
        for(int i = 0; i < finished.length; i++){
            if(!finished[i]) {
                answer[index] = todo_list[i];
                index++;
            }
        }
        
        return answer;
    }
}
```
### 4번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/e256b0e7-ad4e-4667-8e52-5627175c1c4a)

```java
class Solution {
    public int solution(int[] numbers, int n) {
        int answer = 0;
        
        for(int i = 0; i < numbers.length; i++){
            answer += numbers[i];
            if(answer > n) break;
        }
        
        return answer;
    }
}
```

### 5번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/458689d7-44f5-4806-832a-10956300ea88)

```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        int[] answer = new int[arr.length];
        
        for(int i = 0; i < queries.length; i++){
            int [] query = queries[i];
            int s = query[0];
            int e = query[1];
            
            for(int j = s; j <= e; j++){
                arr[j]++;
            }
            
        }
        answer = arr;
        return answer;
    }
}
```


## 13일차

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

### 3번 문제
<img width="771" alt="image" src="https://github.com/xoghkscc/codingTest/assets/82793713/d3f840b0-f07b-4592-8740-17a0899d7792">

```java
class Solution {
    public String[] solution(String[] str_list) {
        String[] answer = {};
        
        int find_index = 0; // 최초 l 혹은 r의 위치를 담을 변수
        String type = ""; // 최초가 l인지 r인지 구분하는 타입을 담을 변수
        
        for(int i = 0; i < str_list.length; i++){
            find_index++;
            if(str_list[i].equals("l")){
                type = "l";
                break; //찾았다면 반복문 탈출
            } else if(str_list[i].equals("r")){
                type = "r";
                break; //찾았다면 반복문 탈출
            }
        }
        
        if(type.equals("l")){
            answer = new String[find_index-1];
            for(int i = 0; i < find_index-1; i++){
                answer[i] = str_list[i]; // 최초가 l이라면 find_index기준 왼쪽에 있는 문자열 담기
            }
        } else if(type.equals("r")){
            answer = new String[str_list.length - find_index];
            for(int i = 0; i < str_list.length - find_index; i++){
                answer[i] = str_list[find_index+i]; // 최초가 l이라면 find_index기준 오른쪽에 있는 문자열 담기
            }
        }  
        return answer;
    }
}
```

* 느낀점: 최초에 나오는 문자열이 l 혹은 r일때 조작해야하는 방법이 달라서 type 문자열을 받아서 했는데 코드가 너무 난잡한 느낌이다.


### 4번 문제
<img width="762" alt="image" src="https://github.com/xoghkscc/codingTest/assets/82793713/be0eaa34-0b52-4fc8-8bca-7fe8eb3f6cd2">

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] num_list, int n) {
        int[] answer = Arrays.copyOfRange(num_list, 0, n);
        return answer;
    }
}
```

* 느낀점:Arrays.copyOfRange(원본 배열, 복사할 시작 인덱스, 복사할 끝 인덱스)-배열을 복사하는 메서드를 배열 문제에서 많이 활용해야할 것 같다.

### 5번 문제
<img width="757" alt="image" src="https://github.com/xoghkscc/codingTest/assets/82793713/221e9523-79bf-449e-8047-a5c21cd2afb9">

```java
class Solution {
    public int[] solution(int[] num_list, int n) {
       
        int length = ((num_list.length - 1) / n) + 1; // num_list의 첫번째 수는 무조건 들어가기에 두번째부터 개수를 센 뒤 n으로 나우었을 때 몫 + 1이 개수이다.
        int[] answer = new int[length];
        
        for(int i = 0; i*n <num_list.length; i++ ){
            answer[i] = num_list[i*n];
        }
        
        return answer;
    }
}
```



