# 876. Middle of the Linked List

### Approach:
We can utilize a two pointer approach: slow and fast. Where slow moves forward once, and fast moves forward twice during each iteration. We traverse until fast becomes "null" (end of the list) then simply return our slow pointer node.

### Code:
```
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
}
```