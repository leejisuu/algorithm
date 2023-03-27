https://www.inflearn.com/course/%EC%9E%90%EB%B0%94-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%AC%B8%EC%A0%9C%ED%92%80%EC%9D%B4-%EC%BD%94%ED%85%8C%EB%8C%80%EB%B9%84/dashboard

[인프런]자바(Java) 알고리즘 문제풀이 입문: 코딩테스트 대비  

65. 경로 탐색(인접행렬) - 배열(정점의 수 가 적을 때)

> 문제 설명   
> 
> 방향 그래프가 주어지면 1번 정점에서 N번 정점으로 가는 모든 경로의 가지 수 를 출력하는 프로그램을 작성하세요.


```java
import java.util.Scanner;

public class Main {
    static int n, m, answer = 0;
    static int[][] graph;
    static int[] chk;

    public void DFS(int v) {
        if(n == v) answer++;
        else {
            for(int i = 1; i <= n; i++) {
                if(graph[v][i] == 1 && chk[i] == 0) { // 간선이 있고,  이미 들리지 않았다면
                    chk[i] = 1;
                    DFS(i); // 백하면 이 라인으로 돌아오기때문에 돌아오면 밑에서 들렸다는 체크를 풀어줘야함
                    chk[i] = 0;
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        n = sc.nextInt(); // 노드의 수
        m = sc.nextInt(); // 간선의 수

        int[][] arr = new int[n+1][n+1];
        for(int i = 0; i < m; i++) {
            int a = sc.nextInt();
            int b = sc.nextInt();
            arr[a][b] = 1;
        }

        chk = new int[n+1];
        chk[1] = 1;
        new Main().DFS(1);

        System.out.println(answer);

    }
}
```