# 203. Remove Linked List Elements

### Approach:
Start by initializing a dummy node then connect that node to the head of the given input (dummy.next = head). We will return that node at the end of the traversal. Next loop through the nodes and skip the node anytime we compare the next node's val with the target value (val). If they happen to match we need to skip the next node (remove it). To do so we simply set curr.next = curr.next.next. Once curr.next == null we can exit our loop and return our original head which we set to dummy.next.

### Code:
```
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode dummy = new ListNode(-1);
        dummy.next = head;
        ListNode curr = dummy;

        while (curr.next != null) {
            if (curr.next.val == val) {
                curr.next = curr.next.next;
            }
            else {
                curr = curr.next;
            }
        }
        return dummy.next;
    }
}
```