# 트리(Tree)

- 노드로 이루어진 계층적 구조

## 용어

- 노드(node) : 트리를 구성하는 기본 원소
  - 루트 노드(root node/root) : 트리에서 부모가 없는 최상위 노드, 트리의 시작점
  - 부모 노드(parent node) : 루트 노드 방향으로 직접 연결된 노드
  - 자식 노드(child node): 루트 노드 반대방향으로 직접 연결된 노드
  - 형제 노드(siblings node): 같은 부모 노드를 갖는 노드들
  - 리프 노드(leaf node/leaf): 자식이 없는 노드
- 경로(path): 한 노드에서 다른 한 노드에 이르는 길 사이에 있는 노드들의 순서
- 길이(length): 출발 노드에서 도착 노드까지 거치는 간선의 개수
- 깊이(depth): 루트 경로의 길이
- 레벨(level): 루트 노드(level=0)부터 노드까지 연결된 간선 수의 합
- 높이(height): 가장 긴 루트 경로의 길이
- 차수(degree): 각 노드의 자식의 개수

## 구현

Tree 클래스

```java
public class Tree {
  int count;
	
	public Tree() {
		count = 0;
	}
	
	public class Node {
		Object data;
		Node left;
		Node right;
	
		// 생성 시 매개변수를 받아 초기화하는 방법으로만 선언 가능
		public Node(Object data) {
			this.data = data;
			left = null;
			right = null;
		}
 
		public void addLeft(Node node) {
			left = node;
			count++;
		}
 
		public void addRight(Node node) {
			right = node;
			count++;
		}
 
		public void deleteLeft() {
			left = null;
			count--;
		}
 
		public void deleteRight() {
			right = null;
			count--;
		}
	}
	
	public Node addNode(Object data) {
		Node n = new Node(data);
		return n;
	}
	
	public void preOrder(Node node) {
		if(node == null) {
			return;
		}
		
		System.out.print(node.data + " ");
		preOrder(node.left);
		preOrder(node.right);
	}
 
	public void inOrder(Node node) {
		if(node == null) {
			return;
		}
		
		inOrder(node.left);
		System.out.print(node.data + " ");
		inOrder(node.right);
	}
 
	public void postOrder(Node node) {
		if(node == null) {
			return;
		}
		
		postOrder(node.left);
		postOrder(node.right);
		System.out.print(node.data + " ");
	}
}
```

## Reference

https://en.wikipedia.org/wiki/Tree_(data_structure)