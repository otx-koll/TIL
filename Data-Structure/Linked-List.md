# 연결 리스트
연결리스트는 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식의 데이터 구조이다. 데이터를 담고 있는 노드들이 연결되어 있고 노드의 포인터는 앞, 뒤 노드를 연결한다. 

## 종류
- 단일 연결 리스트(Singly Linked List)
  - 각 노드가 다음 노드에 대해서만 참조하는 가장 단순한 형태의 연결 리스트
  - 일반적으로 큐를 구현할 때 사용한다.
- 이중 연결 리스트(Doubly Linked List)
  - 각 노드가 이전 노드, 다음 노드에 대해 참조하는 형태의 연결 리스트
  - 삭제가 간편하다.
- 원형 연결 리스트(Circular Linked List)
  - 연결 리스트에서 마지막 요소가 첫번째 요소를 참조
  - 스트림 버퍼 구현에 많이 사용된다.

## 구현
```java
class ListNode{
    private String data;    // 데이터 저장 변수
    public ListNode link;    // 다른 노드를 참조할 링크 노드
    
    public ListNode() {
        this.data = null;
        this.link = null;
    }

    public ListNode(String data) {
        this.data = data;
        this.link = null;
    }

    public ListNode(String data, ListNode link) {
        this.data = data;
        this.link = link;
    }

    public String getData() {
        return this.data;
    }
}

```

