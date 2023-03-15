https://school.programmers.co.kr/learn/courses/30/lessons/12951  

[Java]JadenCase 문자열 만들기

```java
import java.util.*;

class Solution {
    public String solution(String s) {
        String answer = "";

        // 공백을 기준으로 문자열 분할
        String[] array = s.split(" "); 

        for(String str : array) {
            // 문자열의 길이가 0이면 공백이므로 공백 더하기
            if(str.length() == 0) {
                answer += " ";
            } else {
                // 문자열의 첫 글자는 대문자로 변환
                answer += str.substring(0, 1).toUpperCase();
                // 문자열의 첫 글자 제외한 나머지 글자들 소문자로 변환
                answer += str.substring(1).toLowerCase();
                // 한 단어의 변환이 끝나면 공백 더해주기
                answer += " ";
            }
        }

        // 원본 문자열의 마지막 문자가 공백이면 그대로 answer 반환
        if(s.substring(s.length()-1, s.length()).equals(" ")) {
            return answer;
        }

        // 원본 문자열의 마지막 글자가 공백이 아니므로 공백을 제거한 후 반환
        return answer.substring(0, answer.length()-1);
    }
}
```
