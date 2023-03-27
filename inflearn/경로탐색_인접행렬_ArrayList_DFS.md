https://www.inflearn.com/course/%EC%9E%90%EB%B0%94-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%AC%B8%EC%A0%9C%ED%92%80%EC%9D%B4-%EC%BD%94%ED%85%8C%EB%8C%80%EB%B9%84/dashboard

[인프런]자바(Java) 알고리즘 문제풀이 입문: 코딩테스트 대비

66. 경로 탐색(인접행렬) - ArrayList(정점의 수 가 많을 때)

> 문제 설명
>
> 방향 그래프가 주어지면 1번 정점에서 N번 정점으로 가는 모든 경로의 가지 수 를 출력하는 프로그램을 작성하세요.


```java
import java.util.ArrayList;
import java.util.Scanner;

public class Main {
    static int n, m, answer = 0; // n : 노드의 수, m : 간선의 수
    static ArrayList<ArrayList<Integer>> graph; // 노드에 대한 방향그래프 정보를 담는 변수
    static int[] chk; // 노드 방문 여부 담을 배열

    public void DFS(int v) {
        if(v == n) answer++;
        else {
            // graph.get(v) 하여 꺼내면 v에서 다음으로 갈 수 있는(화살표로 가리키는) 노드들의 리스트 반환
            for(int nextV : graph.get(v)) {
                if(chk[nextV] == 0) { // 방문하지 않은 노드들만 방문 할 수 있음
                    chk[nextV] = 1;
                    DFS(nextV);
                    chk[nextV] = 0;
                }
            }
        }
    }

    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        n = sc.nextInt(); // 노드의 수
        m = sc.nextInt(); // 간선의 수
        chk = new int[n+1]; // 노드 방문 여부 담을 배열
        graph = new ArrayList<>();
        Main main = new Main();

        for(int i = 1; i <= n; i++) { // 노드의 수 만큼 ArrayList<Integer> 생성
            graph.add(new ArrayList<>());
        }

        for(int i = 0; i < m; i++) { // 간선의 수 만큼 반복문을 돌며 예를 들어 1 2 입력 받으면 1 -> 2 이며 a = 1, b = 2
            int a = sc.nextInt();
            int b = sc.nextInt();
            graph.get(a).add(b);
        }

        chk[1] = 1;
        main.DFS(1);
        System.out.println(answer);
    }
}
```