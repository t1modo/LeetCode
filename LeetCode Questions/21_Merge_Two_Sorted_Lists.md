# 21. Merge Two Sorted Lists

### Approach:
We can use a recursive approach to merge two sorted linked lists. The function takes two linked lists, list1 and list2, as input and returns a new sorted linked list that merges both. The approach begins by checking whether both lists are non-null. If both lists have nodes, it compares the values of the current nodes. If list1.val is smaller, it recursively calls mergeTwoLists on the next node of list1 and list2, setting the next pointer of list1 to the result of this recursive call. This ensures that the smaller node is correctly placed while the remaining portion of the list is merged in subsequent calls. If list2.val is smaller or equal, a similar process occurs, setting list2.next to the result of recursively merging list1 with list2.next. This ensures that nodes remain in sorted order as recursion unwinds. If either list is null, the function simply returns the other list since no further merging is required.

### Code:
```
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
                list1.next = mergeTwoLists(list1.next, list2);
                return list1;
            }
            else {
                list2.next = mergeTwoLists(list1, list2.next);
                return list2;
            }
        }
        if (list1 == null) {
            return list2;
        }
        else {
            return list1;
        }
    }
}
```