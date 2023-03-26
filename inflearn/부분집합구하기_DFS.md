https://www.inflearn.com/course/%EC%9E%90%EB%B0%94-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%AC%B8%EC%A0%9C%ED%92%80%EC%9D%B4-%EC%BD%94%ED%85%8C%EB%8C%80%EB%B9%84/dashboard

[인프런]자바(Java) 알고리즘 문제풀이 입문: 코딩테스트 대비

59. 부분집합 구하기(DFS)

```java
import java.util.Scanner;

public class Main {
    static int n; // 자연수 n
    static int[] chk; // 자연수 n의 부분집합 사용 여부 체크 할 배열

    public void DFS(int L) {
        // L이 자연수 n의 범위를 넘어갔다면
        if(L == n+1) {
            String temp = "";
            for(int i = 1; i <= n; i++) {
                if (chk[i] == 1) { // 배열의 요소가 1인 인덱스만 더해주기
                    temp += (i + " ");
                }
            }
            if(temp.length() > 0) { // 공집합은 제외
                System.out.println(temp);
            }
        } else {
            chk[L] = 1; // 사용 O
            DFS(L+1); // lt
            chk[L] = 0; // 사용 X
            DFS(L+1); // rt
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        n = sc.nextInt();
        chk = new int[n+1];

        Main main = new Main();
        main.DFS(1);

    }
}
```