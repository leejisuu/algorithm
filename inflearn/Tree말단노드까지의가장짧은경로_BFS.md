https://www.inflearn.com/course/%EC%9E%90%EB%B0%94-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%AC%B8%EC%A0%9C%ED%92%80%EC%9D%B4-%EC%BD%94%ED%85%8C%EB%8C%80%EB%B9%84/dashboard

[인프런]자바(Java) 알고리즘 문제풀이 입문: 코딩테스트 대비

63. Tree 말단 노드까지의 가장 짧은 경로(BFS)

```java
import java.util.*;

class Node {
    int data;
    Node lt, rt;

    public Node(int data) {
        this.data = data;
        this.lt = this.rt = null;
    }
}
public class Main {
    Node root;

    public int BFS(Node root) {
        int level = 0;
        Queue<Node> queue = new LinkedList<>();
        queue.offer(root);

        while(!queue.isEmpty()) {
            int qLen = queue.size();
            for(int i = 0; i < qLen; i++) {
                Node curNode = queue.poll();
                if(curNode.lt == null && curNode.rt == null) { // 말단노드는 양쪽 자식이 모두 없는 노드
                    return level;
                }
                if(curNode.lt != null) {
                    queue.offer(curNode.lt);
                }
                if(curNode.rt != null) {
                    queue.offer(curNode.rt);
                }
            }
            level++;
        }

        return -1;
    }

    public static void main(String[] args) {
        Main main = new Main();
        main.root = new Node(1);
        main.root.lt = new Node(2);
        main.root.rt = new Node(3);
        main.root.lt.lt = new Node(4);
        main.root.lt.rt = new Node(5);

        System.out.println(main.BFS(main.root));
    }
}
```