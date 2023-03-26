https://www.inflearn.com/course/%EC%9E%90%EB%B0%94-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%AC%B8%EC%A0%9C%ED%92%80%EC%9D%B4-%EC%BD%94%ED%85%8C%EB%8C%80%EB%B9%84/dashboard

[인프런]자바(Java) 알고리즘 문제풀이 입문: 코딩테스트 대비

58. 이진트리순회(DFS : Depth-First Search)

```java
class Node {
    int data;
    Node lt, rt;

    public Node(int data) {
        this.data = data;
        this.lt = this.rt = null;
    }
}

public class Tree {
    Node root;

    public static void main(String[] args) {
        Tree tree = new Tree();
        tree.root = new Node(1);
        tree.root.lt = new Node(2);
        tree.root.rt = new Node(3);
        tree.root.lt.lt = new Node(4);
        tree.root.lt.rt = new Node(5);
        tree.root.rt.lt = new Node(6);
        tree.root.rt.rt = new Node(7);

        System.out.println("전위 순회");
        tree.pre(tree.root);
        System.out.println();

        System.out.println("중위 순회");
        tree.in(tree.root);
        System.out.println();

        System.out.println("후위 순회");
        tree.post(tree.root);
    }

    public void pre(Node node) {
        if(node == null) return;

        System.out.print(node.data + " ");
        pre(node.lt);
        pre(node.rt);
    }

    public void in(Node node) {
        if(node == null) return;

        in(node.lt);
        System.out.print(node.data + " ");
        in(node.rt);
    }

    public void post(Node node) {
        if(node == null) return;

        post(node.lt);
        post(node.rt);
        System.out.print(node.data + " ");
    }
}
```