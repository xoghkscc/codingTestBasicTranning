# codingTest 기초 트레이닝

## 참고할 사이트
### https://earthteacher.tistory.com/169#gsc.tab=0

## 19일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/9c777704-101c-43a6-bcf0-03982b749258)

```java
import java.util.*;

class Solution {
    public String[] solution(String myStr) {
        
        myStr = myStr.replace("a", " ");
        myStr = myStr.replace("b", " ");
        myStr = myStr.replace("c", " ");

        //myStr = myStr.replaceAll("a|b|c", " "); 정규표현식으로 위 3줄을 한번에 가능
        
        String[] myStrArr = myStr.split(" ");
        ArrayList<String> list = new ArrayList<>();
        
        for(String str : myStrArr){
            if(!str.isEmpty()) list.add(str);
        }
        
        if(list.isEmpty()) list.add("EMPTY");

        return list.toArray(new String[list.size()]);
    }

}
```

### 2번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/515e6d84-e734-47ef-9a09-55218b9df594)

```java
import java.util.*;

class Solution {
    public int[] solution(int[] arr) {
        ArrayList<Integer> list = new ArrayList<>();
        
        for(int num : arr){
            for(int i = 0; i < num; i++){
                list.add(num);
            }
        }
                
        int[] answer = new int[list.size()];
        
        for(int i = 0; i < list.size(); i++){
            answer[i] = list.get(i);
        }

        return answer;
    }
}
```

*    느낀점: lsit.toArray 메서드는 String일때만 가능하고 int 배열은 불가능하다.

### 3번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/5a40b4bc-0b25-4e4b-98f5-de0bea7e8b1b)

```java
import java.util.*;

class Solution {
    public int[] solution(int[] arr, boolean[] flag) {
        
        ArrayList<Integer> list = new ArrayList<>();
        
        for(int i = 0; i < arr.length; i++){
            if(flag[i]){
                for(int j = 0; j < arr[i]*2; j++){
                    list.add(arr[i]);
                }
            } else {
                for(int j = 0; j < arr[i]; j++){
                    list.remove(list.size()-1);
                }
            }
        }
        
        int[] answer = new int[list.size()];
        
        for(int i = 0; i < list.size(); i++){
            answer[i] = list.get(i);
        }

        return answer;
    }
}
```

### 4번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/5847aa59-c1d8-4ece-bfa9-cf72bab06189)

```java
import java.util.*;

class Solution {
    public int[] solution(int[] arr) {
        Stack<Integer> stack = new Stack<>();
        
        for(int num : arr){
            if(stack.isEmpty() || stack.peek() != num) {
                stack.push(num);
            } else {
                stack.pop();
            }
        }
        
        if(stack.isEmpty()) stack.push(-1);
    
        Object[] object = stack.toArray();
        
        int[] answer = new int[stack.size()];
        
        for(int i = 0; i < stack.size(); i++){
            answer[i] =(int) object[i];
        }
        
        return answer;
    }
}
```

## 18일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/e2266d29-67e1-4cd0-ba1d-0522cac5d594)

```java
class Solution {
    public int[] solution(String myString) {
        myString = myString + "a"; //뒤에 x를 제외한 임의의 수를 붙인다.
        
        String[] strArr = myString.split("x");

        int[] answer = new int[strArr.length];
        
        for(int i = 0; i < strArr.length; i++){
            answer[i] = strArr[i].length();
        }
        
        answer[strArr.length - 1]--; //뒤에 임의의 수를 붙였기 때문에 그만큼의 길이인 1을 뺀다.

        //String[] result = myString.split("x", myString.length());
        //로 split하면 맨 끝이 x라도 빈 값으로 split함

        return answer;
    }
}
```

*    문제의 조건는 x가 끝에 올 경우에도 나눠진 문자열의 길이는 0으로 제시하였는데 split을 할 경우 x가 맨 끝에 오는 경우는 null로 체크되어 길이 자체가 존재하지 않는다.
     예를 들어 oxoox -> [o, oo] -> [1, 2] 그러나 문제의 의도는 [o, oo, ] -> [1, 2, 0]
     그렇기 때문에 맨 끝에 임의의 수 a를 둬서 oxooxa -> [o, oo, a] -> [1, 2, 1-1]로 문제를 해결하였다.
     만약 맨끝이 x가 아니더라도 oxooxoa -> [o, oo, oa] -> [1, 2, 2-1] -> [1, 2, 1]로 해결완료 


### 2번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/4b3a1670-b166-45b7-a1d3-7cacf16684a0)

```java
import java.util.*;
class Solution {
    public String[] solution(String myString) { 
        ArrayList<String> strList = new ArrayList<String>();
        String[] answer = {};
        
        String [] strArray = myString.split(""); //문자 단위로 split
        
        String str = "";
        
        for(int i = 0; i < strArray.length; i++){
            if(!strArray[i].equals("x")){
                str += strArray[i];
                if(i == strArray.length -1 ) strList.add(str); // 마지막 문자가 x가 아니면서 끝날 경우 리스트에 담아줘야함
            } else if(!str.isEmpty()){
                strList.add(str); 
                str = "";
            }
        }

        //사전순으로 정렬
        for(int i = 0; i < strList.size(); i++){
            for(int j = 0; j < strList.size(); j++){
                if(strList.get(i).compareTo(strList.get(j)) < 0){
                    String tmp = strList.get(i);
                    strList.set(i, strList.get(j));
                    strList.set(j, tmp);
                }
            }
        }

        answer = strList.toArray(new String[strList.size()]);
        
        return answer;
    }
}
```

#### 다른 사람의 풀이
```java
class Solution {

    public String[] solution(String myString) {
        String[] tmp = myString.split("x");
        Arrays.sort(tmp);
        ArrayList <String> list = new ArrayList<>();

        for (int i = 0; i < tmp.length; i++) {
            if (!tmp[i].equals("")) {
                list.add(tmp[i]);
            }
        }

        String[] answer = new String[list.size()];

        for (int i = 0; i < answer.length; i++) {
            answer[i] = list.get(i);
        }

        return answer;
    }
}
```

*    문자열을 자르는 방식이 힘든것 같다. 다른 사람의 풀이처럼 처음부터 x로 자르고 리스트로 ""이 아닌 것을 받는 것이 더 수월할 것 같다. 또한 앞으로 정렬할 때에는 sort 메서드를 활용하자.

### 3번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/15be3828-c898-4cf0-a77e-dde992ba5da1)

```java
class Solution {
    public int solution(String binomial) {
        int answer = 0;
        
        String[] binomialArray = binomial.split(" ");
      
        int a = Integer.parseInt(binomialArray[0]);
        String op = binomialArray[1];
        int b = Integer.parseInt(binomialArray[2]);

        switch(op){
            case "+":
                answer = a + b;
                break;
            case "-":
                answer = a - b;
                break;
            case "*":
                answer = a * b;
                break;
        }
        return answer;
    }
}
```


### 4번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/17f5b8a0-f8e4-4920-8c11-9c21615fdb5f)

```java
class Solution {
    public int solution(String myString, String pat) {
        int answer = 0;
        
        String chgString = "";
        
        for(int i = 0; i < myString.length(); i++){
            if(myString.charAt(i) == 'A') {
                chgString += "B";
            }else if(myString.charAt(i) == 'B') {
                chgString += "A";
            } else {
                chgString += myString.charAt(i);
            }
        } 
        answer = chgString.indexOf(pat) > -1 ? 1 : 0;
        
        return answer;
    }
}
```

#### 다른 사람의 풀이
```java
class Solution {
    public int solution(String myString, String pat) {
        myString = myString.replace("A", "a").replace("B", "A").replace("a", "B"); //대문자를 소문자로 바꿔서....
        return myString.contains(pat) ? 1 : 0;
    }
}
```

### 5번 문제

```java
class Solution {
    public String solution(String rny_string) {
        String answer = rny_string.replace("m", "rn");
        return answer;
    }
}
```

## 17일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/c9c20c04-1d9a-44ac-890e-172f9e4e3e82)

```java
class Solution {
    public String solution(String myString, String pat) {
        String answer = "";
        int lastIndex = myString.lastIndexOf(pat); 
        
        answer = myString.substring(0, lastIndex) + pat;
        
        return answer;
    }
}
```

*    느낀점: 왠지 String 메서드를 많이 안써야할 것 같지만 인터넷을 보고 다른 풀이도 보니 다들 메서드를 많이 활용중인 것 같다.

### 2번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/24013267-e459-453f-aab5-99008178b23c)

```java
class Solution {
    public int solution(String myString, String pat) {
        int answer = 0;
        
        while(true){
            if(myString.indexOf(pat) > -1){
               myString = myString.substring(myString.indexOf(pat)+1, myString.length()); //ex) banana에서 ana가 포함된 index가 1 이므로 substring 2부터인 nana에서 ana 포함된 개수 찾기
               answer++;
            } else {
                break;
            }
        }
        return answer;
    }
}
```

*    느낀점: 핵심은 포함된 단어의 index+1만큼 잘라 다시 포함 조사를 반복해 나가는 것이 특징

### 3번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/3147d151-8872-4d73-82e2-90efc65acb31)

```java
import java.util.*;

class Solution {
    public String[] solution(String[] strArr) {
        Boolean[] booArr = new Boolean[strArr.length];
        
        int count = 0;
        
        for(int i = 0; i < strArr.length; i++){
            if(strArr[i].indexOf("ad") > -1){ 
                booArr[i] = false; //ad가 포함된 경우
            } else {
                booArr[i] = true;  //ad가 포함 안된 경우
                count++;
            }
        }
        
        String[] answer = new String[count];
        
        count = 0;
        
        for(int i = 0; i < strArr.length; i++){
            if(booArr[i]){
                answer[count] = strArr[i];
                count++;
            }
        }
        
        return answer;
    }
}
```

*    느낀점: strArr와 대응하는 booArr을 만들어 strArr의 원소 중 ad라는 문자가 포함되면 booArr 원소는 false 아니면 true 그런데 다들 ArrayList를 만들어서 푸는거 보니 앞으로 변환하는 걸 자주 시도해봐야겟다.

### 4번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/eaf90118-9890-4027-b64f-c7ce5629809a)

```java
class Solution {
    public String[] solution(String my_string) {
        String[] answer = {};
        answer = my_string.split(" ");
        return answer;
    }
}
```


### 5번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/ca121dfd-dc52-43bd-9da0-e5eaf518a0ca)

```java
import java.util.*;
class Solution {
    public String[] solution(String my_string) {
        String[] answer = {};
        
        my_string = my_string.trim(); //양쪽 공백 제거
        
        String[] list = my_string.split(" "); // 공백을 split한 배열 만들기

        List<String> listArray = new ArrayList<String>(); //공백이 아닌 값을 받을 list 만들어주기
       
        for(String str : list){
            if(!str.isEmpty()){
                listArray.add(str);
            }
        }        
        answer = listArray.toArray(new String[listArray.size()]); //리스트를 배열로 반

        return answer;
    }
}
```

*    느낀점: list 사용을 최소화하면서 isEmpty 메서드를 활용

```java
my_string.trim().split("[ ]+"); //정규표현식을 활용하여도 됨
```

## 16일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/04298912-79c8-4692-ad4c-7d870ef4bc16)

```java
class Solution {
    public String solution(String myString) {
        String answer = "";
        answer = myString.toUpperCase();
        return answer;
    }
}
```


### 2번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/f095742c-317d-4d02-b827-1f163c300cd8)

```java
class Solution {
    public String solution(String myString) {
        String answer = "";
        answer = myString.toLowerCase();
        return answer;
    }
}
```

### 3번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/933cbb0b-4a12-4cb7-97e3-f493f621c7a0)

```java
class Solution {
    public String[] solution(String[] strArr) {
        String[] answer = new String[strArr.length];
        
        for(int i = 0; i < strArr.length; i++){
            answer[i] = i % 2 != 0 ? strArr[i].toUpperCase() : strArr[i].toLowerCase(); //삼항연산자 활
        }
        
        return answer;
    }
}
```

### 4번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/96695dbb-3d21-4ce5-a105-5c40a3a22d51)

```java
class Solution {
    public String solution(String myString) {
        String answer = "";
        
        for(int i = 0; i < myString.length(); i++){
           if(myString.charAt(i) == 'a'){
               answer += "A";
           } else if(myString.charAt(i) >= 'B' && myString.charAt(i) <= 'Z'){ //A가 아닌 대문자
               answer += (char) (myString.charAt(i) + 32); //char에 32를 더하면 대문자 -> 소문자 반대로 32를 빼면 소문자 -> 대문자
           } else {
               answer += myString.charAt(i);
           }
        }
        
        return answer;
    }
}
```

### 5번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/1047071d-6219-4ae8-a3f3-5861de86964f)

```java
class Solution {
    public String solution(String my_string, String alp) {
        String answer = "";
        
        answer = my_string.replace(alp, alp.toUpperCase());
        
        return answer;
    }
}
```

## 15일차차

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


### 5번 문제
![image](https://github.com/xoghkscc/codingTest/assets/82793713/374b3ddc-b8b2-493a-ae81-e896821f0630)

```java
class Solution {
    public int solution(String myString, String pat) {
        int answer = 0;
        
        myString = myString.toUpperCase();
        pat = pat.toUpperCase();
        
        answer = myString.contains(pat) ? 1 : 0;
       
        return answer;
    }
}
```

*    contains메서드를 기억해 두자

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



