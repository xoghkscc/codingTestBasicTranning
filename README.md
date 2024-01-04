# codingTest 기초 트레이닝

## 참고할 사이트
### https://earthteacher.tistory.com/169#gsc.tab=0

## 24일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/470901dd-bcb2-48e2-9364-ce8ee8aa4357)

```java
class Solution {
    public int solution(String[] order) {
        int answer = 0;
        
        for(String str : order){
            if(str.contains("latte")){
                answer += 5000;
            } else {
                answer += 4500;
            }
        }     
        return answer;
    }
}
```

### 2번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/7e25cf2b-9664-49f3-97b0-dd164674558b)

```java
import java.util.*;
class Solution {
    public String[] solution(String[] picture, int k) {
        ArrayList<String> list = new ArrayList<>();

        for(String str : picture){                        //.xx...xx.를 가져오자
            for(int i = 0; i < k; i++){                   //2배만큼 list에 더 담아야함
                StringBuilder sb = new StringBuilder();
                for(int j = 0; j < str.length(); j++){    //.을 가져오자
                    for(int l = 0; l < k; l++){
                        sb.append(str.charAt(j));         //.을 2배만큼 sb에 붙인다. -> ..
                    } 
                }                                        //그 다음인 x를 가져온다
                list.add(sb.toString());                 //..xxxx......xxxx..를 넣는다.
            } 
        }
        return list.toArray(new String[list.size()]);
    }
}
```

```java
class Solution {
    public String[] solution(String[] picture, int k) {
        String x = "";
        String y = "";          
        for (int i=0; i<k;i++) { //k배만큼 .과 x를 붙인다.
            x += ".";
            y += "x";
        }
        List<String> list = new ArrayList<>();
        for (int i=0; i<picture.length;i++) {
            for (int j=0;j<k;j++){              
                list.add(picture[i].replaceAll("[.]", x).replaceAll("[x]", y)); //배열의 .과 x를 k배만큼 붙인 것으로 replace를 한다. 그리고 k배만큼 list에 추가!
            }
        }
        return list.stream().toArray(String[]::new);
    }
}
```

### 3번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/9e0f69bb-7eba-4cc9-b19d-3e50415032be)

```java
class Solution {
    public int[] solution(int[] arr, int k) {
        for(int i = 0; i < arr.length; i++){
            if(k % 2 != 0){
                arr[i] *= k;
            } else {
                arr[i] += k;
            }
        }
        return arr;
    }
}
```

### 4번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/2266dde2-32d9-4aab-87c9-1fdc53899d07)

```java
class Solution {
    public String solution(String myString) {
        StringBuilder answer = new StringBuilder();
        
        for(int i = 0; i < myString.length(); i++){
            if(myString.charAt(i) < 'l'){
                answer.append('l');
            } else {
                answer.append(myString.charAt(i));
            }
        }   
        return answer.toString();
    }
}
```
### 5번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/021d25ad-0df9-463c-b84c-4c54acf3fc7d)

```java
class Solution {
    public int[][] solution(int n) {
        int[][] answer = new int[n][n];
        
        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                if(i == j) {
                    answer[i][j] = 1;
                } else {
                    answer[i][j] = 0;
                }
            }
        }
        return answer;
    }
}
```


## 23일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/ca61b987-ebc7-4303-9915-aff8c53858b4)

```java
class Solution {
    public int solution(String str1, String str2) {
        int answer = 0;
        return str2.contains(str1) ? 1 : 0;
    }
}
```

### 2번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/355cab9d-eaaf-4b1a-95db-cb6c20c6c511)

```java
class Solution {
    public String solution(String[] str_list, String ex) {
        StringBuilder sb = new StringBuilder();
        
        for(String str : str_list){
            if(!str.contains(ex)){
                sb.append(str);
            }
        }
        return sb.toString();
    }
}
```

### 3번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/1cd1ed45-ef9e-45df-98bd-c901f615e36b)

```java
class Solution {
    public int solution(int[] num_list, int n) {
        int answer = 0;
        
        for(int num : num_list){
            if(num == n){
                answer = 1;
                break;
            }
        }  
        return answer;
    }
}
```
### 4번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/1f42708e-ac54-4eb7-97e0-96a252205a96)

```java
class Solution {
    public int solution(int a, int b) {
        int answer = 0;
        if(a % 2 == 1 && b % 2 == 1) {
            answer += Math.pow(a, 2) + Math.pow(b, 2);
        } else if(a % 2 != 1 && b % 2 != 1) {
            answer += Math.max(a-b, b-a);
        } else {
            answer += 2*(a+b);
        }   
        return answer;
    }
}
```

### 5번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/efc40aee-411e-4dd4-b970-f7a6d697356b)

```java
class Solution {
    public int solution(int[] date1, int[] date2) {
        StringBuilder data_yyyymmdd1 = new StringBuilder();
        StringBuilder data_yyyymmdd2 = new StringBuilder();
        
        for(int i = 0; i < date1.length; i++){
            data_yyyymmdd1.append("" + date1[i]);
            data_yyyymmdd2.append("" + date2[i]);
            }
        return Integer.parseInt(data_yyyymmdd1.toString()) < Integer.parseInt(data_yyyymmdd2.toString()) ? 1 : 0;
    }
}
```


## 22일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/225b1b45-313b-4164-b5a4-2aa4970f41bb)

```java
class Solution {
    public String solution(String n_str) {
        return Integer.toString(Integer.parseInt(n_str));
    }
}
```

### 2번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/95e272b4-a208-4027-bd3f-45f44d067798)


```java
import java.util.*;

class Solution {
    public String solution(String a, String b) {
        int[] aArray = new int[Math.max(a.length(), b.length())+1];
        int[] bArray = new int[Math.max(a.length(), b.length())+1];
        //두 수를 더해 자릿수가 추가될 수 있으므로 길이는 +1로 한다.

        for(int i = a.length()-1; i >= 0 ; i--){
            aArray[a.length()-1 - i] = Integer.parseInt(a.charAt(i)+"");
        }
        // 숫자의 역순으로 배열을 넣는다 예를 들어 1234 -> [4, 3, 2, 1]
        
        for(int i = b.length()-1; i >= 0 ; i--){
            bArray[b.length()-1 - i] = Integer.parseInt(b.charAt(i)+"");
        }
        // b가 a보다 길이가 작다면 배열의 빈자리는 0으로 채워진다 123 -> [3, 2, 1, 0]
        
        for(int i = 0; i < aArray.length-1; i++){
            int aNum = aArray[i];
            int bNum = bArray[i];

            int tenNum = (aNum + bNum) / 10;
            aArray[i+1] = aArray[i+1] +tenNum; //두 수의 합이 10을 넘어가면 자릿수 올림을 해주는 코드
             
            int oneNum = (aNum + bNum) % 10;
            aArray[i] = oneNum; // 두 수의 합의 일자리를 a배열의 추가한다.
            
        }
        // a배열에는 두 수의 합의 역순이 된다. a: 1234, b:123 -> a배열: [7, 5, 3, 1]
        
        StringBuilder answerStr = new StringBuilder();
        
        for(int i = aArray.length-1; i >= 0 ; i--){
            if(aArray[i] == 0 && i == aArray.length-1) continue; //두 수의 합이 자릿수가 추가가 안될 경우 조합을 제외한다 123+123 -> [6, 4, 2, 0]
            answerStr.append(aArray[i]); //a배열은 숫자 합의 역순으로 하였으므로 조립할때도 역순으로 조힙한다.
        }

        return answerStr.toString();
    }
}
```

### 3번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/de7a3d54-13ab-44bd-b548-6ef6a87b6430)

```java
class Solution {
    public String solution(int n) {  
        return ""+n;
    }
}
```

### 4번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/0b712c48-e775-4cf9-a682-026df737bc03)

```java
import java.util.*;

class Solution {
    public int[] solution(int[] arr, int[] delete_list) {
        ArrayList<String> list = new ArrayList<>();
        
        for(int i = 0; i < arr.length; i++){
            list.add(arr[i]+"");
        }
   
        for(int i = 0; i < delete_list.length; i++){
            list.remove(delete_list[i]+"");
        }

        int[] answer = new int[list.size()];
        
        for(int i = 0; i < answer.length; i++){
            answer[i] =Integer.parseInt(list.get(i));
        }                      
                               
        return answer;
    }
}
```

### 5번문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/f4820f6f-adfd-46e1-b16d-8449bbb69d5b)

```java
class Solution {
    public int solution(String my_string, String target) {
        return my_string.contains(target) ? 1 : 0;
    }
}
```

## 21일차

### 1번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/de2e856a-5c71-4437-898d-f58fde27fb6a)

```java
import java.util.*;

class Solution {
    public int[] solution(int[] num_list) {
        Arrays.sort(num_list);

        int[] answer = new int[num_list.length-5];
        
        for(int i = 5; i < num_list.length; i++){
            answer[i-5] = num_list[i];
        }
        
        return answer;
    }
}
```

### 2번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/84c8b451-a993-4fc3-99cd-ea9acc504968)

```java
import java.util.*;

class Solution {
    public int solution(int[] rank, boolean[] attendance) {
        ArrayList<Integer> list = new ArrayList<>();
        
        for(int i = 0; i < rank.length; i++){
            list.add(rank[i]);
        }

        int answer = 0;
        int cnt = 0;
        int index = 10000;
        for(int i = 0; i < rank.length; i++){
            if(attendance[list.indexOf(i+1)]){
                answer += index*list.indexOf(i+1);
                index = index/100;
                cnt++;
            }
            
            if(cnt == 3) break;
        }
        
        return answer;
    }
}
```

*    핵심은 list.indexOf를 통해 해당 위치(학생번호)를 찾아내는 것 또한 HashMap을 통해 map.put(rank[i], i)를 하면 key대로 정렬되므로 더 쉽게 가


```java
//다른 사람의 풀이
import java.util.*;
class Solution {
    public int solution(int[] rank, boolean[] attendance) {
        int ans = 0, cnt = 0, r = 1;
        int[] abc = new int[3];
        HashMap<Integer,Integer> m = new HashMap<>();
        for(int i=0 ; i<rank.length ; i++)
            m.put(rank[i],i);
        while(cnt<3){
            if(attendance[m.get(r)])
                abc[cnt++] = m.get(r);
            r++;
        }
        return abc[0]*10000 + abc[1]*100 + abc[2];
    }
}
```

### 3번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/e122d7d2-98f7-4db5-ab51-6acb57fa793d)

```java
class Solution {
    public int solution(double flo) {
        return (int) flo;
    }
}
```

### 4번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/77ba825c-bedd-41cd-b1ed-02940c9bf050)

```java
class Solution {
    public int solution(String num_str) {
        int answer = 0
        for(int i = 0; i < num_str.length(); i++){
            answer += Integer.parseInt(""+num_str.charAt(i));
        }
        return answer;
    }
}
```

### 5번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/8a836f21-2395-4f22-8e07-846b91e662da)

```java
class Solution {
    public int solution(String n_str) {
        return Integer.parseInt(n_str);
    }
}
```

## 20일자

### 1번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/2068ad38-e4c6-4979-b980-9bbd23abcc13)

```java
class Solution {
    public int[] solution(int[] arr) {
        int index = 0;
        
        while(true){
            if(Math.pow(2, index) == arr.length){
                break;
            } else if(Math.pow(2, index) < arr.length && Math.pow(2, index+1) > arr.length){
                index++;
                break;
            } else {
                index++;
            }
        }
        
        int[] answer = new int[(int) Math.pow(2, index)]; //Math.pow는 double타입이므로 int타입으로 형변환 필
        
        for(int i = 0; i < answer.length; i++){
            if(i < arr.length){
                answer[i] = arr[i];
            } else {
                answer[i] = 0;
            }
        }

        // return Arrays.copyOf(arr, (int) Math.pow(2, index)); 애초에 배열의 빈요소는 int타입에서는 0이 들어가기 때문에 이를 이용해도 됨
        
        return answer;
    }
}
```

### 2번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/896e17dd-ee74-4794-8d79-9b1962864f31)

```java
class Solution {
    public int solution(int[] arr1, int[] arr2) {

        int arrLength1 = arr1.length;
        int arrLength2 = arr2.length;
        
        int arrSum1 = 0;
        int arrSum2 = 0;
        
        for(int i = 0; i < Math.min(arrLength1, arrLength2); i++){
            arrSum1 += arr1[i];
            arrSum2 += arr2[i];
        }
        
        int answer = 0;
        
        if(arrLength1 > arrLength2) {
            answer = 1;
        } else if(arrLength1 < arrLength2) {
            answer = -1;
        } else if(arrSum1 > arrSum2) {
            answer = 1;
        } else if(arrSum1 < arrSum2) {
            answer = -1;
        }
        
        
        return answer;
    }
}
```

### 3번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/3985ebed-095d-4456-8236-999ae28a2c0f)

```java
import java.util.*;

class Solution {
    public int solution(String[] strArr) {
        ArrayList<Integer> lengthList = new ArrayList<>();
        
        for(String str : strArr){
            lengthList.add(str.length());
        }
        
        Collections.sort(lengthList); // 길이 순서대로 정렬

        int maxCount =0;
        
        for(int i = 0; i < lengthList.size(); i++){
            int firstIndex = lengthList.indexOf(lengthList.get(i));
            int lastIndex = lengthList.lastIndexOf(lengthList.get(i));
            
            if((lastIndex - firstIndex + 1) > maxCount) maxCount = lastIndex - firstIndex + 1; //즉 해당 숫자의 마지막 인덱스와 첫 인덱스를 빼고 +1한 것이 해당 숫자의 개수임
            
            i = lastIndex; // 중복할 필요 없으므로 i는 해당 숫자의 마지막 인덱스로 넘겨버
            
        }
        return maxCount;
    }
}
```
### 4번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/fced4f2a-2039-46ef-bd17-0d31bd9f3d92)

```java
class Solution {
    public int[] solution(int[] arr, int n) {
        for(int i = arr.length%2; i < arr.length; i = i + 2){
            arr[i+1] = arr[i+1] + n;
        }
        
        if(arr.length%2 == 1) arr[0] = arr[0] + n;

        return arr;
    }
}
```

### 5번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/fe151f95-1cf7-4f28-a0b8-4083aa8e7171)

```java
import java.util.*;

class Solution {
    public int[] solution(int[] num_list) {
        Arrays.sort(num_list);
        
        return Arrays.copyOfRange(num_list, 0, 5);
    }
}
```

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

### 5번 문제
![image](https://github.com/xoghkscc/codingTestBasicTranning/assets/82793713/7cc757c4-98b2-4227-83e0-c7e532b705e3)

```java
import java.util.*;

class Solution {
    public int[] solution(int[] arr, int k) {
        ArrayList<Integer> list = new ArrayList<>();
        
        for(int i = 0; i < arr.length; i++){
            if(list.indexOf(arr[i]) == -1){
                list.add(arr[i]);
            }
            
            if(list.size() == k) break;
        }
        
        if(list.size() < k) {
            while(true){
                list.add(-1);
                
                if(list.size() == k) break;
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



