## Stack
- 데이터를 책을 쌓아놓는 것처럼 순서대로 쌓는 자료구조
- 후입선출(Last In First Out)
- 단뱡항 입출력 구조
- 깊이 우선 탐색(DFS)에 이용됨
- 재귀적 함수를 호출할 때 사용
## Stack 선언
```java
import java.util.Stack;
Stack<Integer> stack = new Stack<>(); // int형
Stack<String> stack = new Stack<>(); // String형
```
## Stack 값 추가 및 삭제
```java
Stack<String> stack = new Stack<>();
stack.push("A");     // stack에 값 A 추가
stack.push("B");     // stack에 값 B 추가
stack.push("C");     // stack에 값 C 추가
stack.pop();         // stack에 값 제거
stack.clear();       // stack의 값 전체 제거
```

## Stack의 가장 상단 값 출력
```java
Stack<String> stack = new Stack<>();
stack.push("A");     // stack에 값 A 추가
stack.push("B");     // stack에 값 B 추가
stack.push("C");     // stack에 값 C 추가
stack.peek();        // stack의 가장 상단 값 출력
```
## Stack의 기타 메서드
```java
Stack<String> stack = new Stack<>();
stack.push("A");     // stack에 값 A 추가
stack.push("B");     // stack에 값 B 추가
stack.size();        // stack의 크기 출력 : 2
stack.empty();       // stack이 비어 있는지 확인(비어있으면 true)
stack.contains("A"); // stack에 A가 있는지 확인(있으면 true)
stack.search("C");   // 해당 요소 위치(빠져나오는 순서)(찾는 값 없으면 -1 반환)
```
## Reference

https://en.wikipedia.org/wiki/Stack_(abstract_data_type)

https://coding-factory.tistory.com/601