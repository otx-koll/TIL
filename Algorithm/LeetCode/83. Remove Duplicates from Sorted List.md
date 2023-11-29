## Description
Given the `head` of a sorted linked list, _delete all duplicates such that each element appears only once._ Return _the linked list **sorted** as well_.

중복 항목 삭제 후, 정렬된 연결리스트 반환 

**Example 1:**

> **Input:** head = [1,1,2]
> 
> **Output:** [1,2]

**Example 2:**

> **Input:** head = [1,1,2,3,3]
> 
> **Output:** [1,2,3]
 
**Constraints:**

- The number of nodes in the list is in the range `[0, 300]`.
- `-100 <= Node.val <= 100`
- The list is guaranteed to be **sorted** in ascending order.

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
```
## Solution
### Code
```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        /*
        approach
        현 노드 값과 다음 노드의 값을 비교해서 같다면 다음 노드를 다다음 노드로 업데이트해준다. 이렇게 중복제거를 하고,
        값이 같지 않다면 현 노드를 다음 노드로 이동해서 순회를 계속 한다.

        time complexity : O(n)

        review
        조금 해맸지만 수월하게 했다
        */
        ListNode list = head;

        while(list != null && list.next != null) {
            if(list.val == list.next.val) {
                list.next = list.next.next;
            } else {
                list = list.next;
            }
        }
        return head;
    }
}
```

### Related
[Linked List](/Data-Structure/Linked-List.md)

### See also
https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/