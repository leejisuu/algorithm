```java
import java.util.*;

public class Main {

    public int BFS(int s, int e) {
        Queue<Integer> queue = new LinkedList<>();
        int[] dis = {1, -1, 5};
        int[] chk = new int[10001];
        int level = 0;

        // root 값 세팅
        chk[s] = 1;
        queue.offer(s);

        while(!queue.isEmpty()) {
            int qLength = queue.size();
            for(int i = 0; i < qLength; i++) {
                int curNum = queue.poll();
                /*
                if(curNum == e) {
                    return level;
                }
                 */

                for(int d : dis) {
                    int temp = curNum + d;
                    if(temp == e) {
                        return level + 1;
                    }
                    if(temp >= 1 && temp <= 10000 && chk[temp] == 0) {
                        chk[temp] = 1;
                        queue.offer(temp);
                    }
                }
            }
            level++;
        }

        return -1;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int s = sc.nextInt();
        int e = sc.nextInt();

        System.out.println(new Main().BFS(s, e));
    }

}
```