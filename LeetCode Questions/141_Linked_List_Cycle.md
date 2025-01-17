# 141. Linked List Cycle

### Approach:
Before we start checking using a slow and fast pointer, we need to ensure the length of the head we are given is long enough to even contain a cycle. Handle the edge case if either head == null or head.next == null. Assuming the head has a sufficient length, we can utilize two pointers: slow and fast. Slow will iterate once each pass, while fast iterates twice. If the values of slow ever equals fast, we have detected a cycle.

### Approach:
```
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        }
        ListNode slow = head;
        ListNode fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                return true;
            }
        }
        return false;
    }
}
```