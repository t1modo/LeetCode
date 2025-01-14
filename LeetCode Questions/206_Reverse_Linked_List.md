# 206. Reverse Linked List

### Approach:
We can use three pointers (curr, prev, and temp) to manipulate the list in-place without requiring additional storage for nodes. Initially, prev is set to null to represent the new tail of the reversed list, and curr is set to the head of the original list. The function iterates through the list until curr becomes null, signifying the end of the list. During each iteration, the temp pointer temporarily stores the next node (curr.next) to ensure the traversal continues. The curr.next pointer is redirected to prev, effectively reversing the link for the current node. Then, prev is updated to the current node, and curr is advanced to the next node using temp. At the end of the loop, prev points to the new head of the reversed list, which is returned as the result.

### Code:
```
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode curr = head;
        ListNode prev = null;
        ListNode temp = null;
        while (curr != null) {
            temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        return prev;
    }
}
```