# 287. Find the Duplicate Number

### Approach:
The problem can be visualized as representing the input array nums as a linked list. In this conceptualization, each element in the array acts as a pointer to the index it references. For example, if an element at index i has a value 2, it implies a pointer from index i to index 2. Since there is one duplicate in the array, this forms a cycle in the "linked list." The goal is to find the entry point of this cycle, which corresponds to the duplicate number.

To solve the problem, we use Floyd's Cycle Detection Algorithm, also known as the "Tortoise and Hare" algorithm.

First we need to detect the cycle. We initialize two pointers, slow and fast, both starting at index 0. Starting at 0 is appropriate because there is guaranteed to be no cycle at 0 since our index range is [1, n]. The slow pointer moves one step at a time (nums[slow]), while the fast pointer moves two steps at a time (nums[nums[fast]]). If there is a cycle (which we know exists because of the duplicate), the slow and fast pointers will eventually meet inside the cycle.

Next we need to find the entry point of the cycle. Once the slow and fast pointers meet, we reset one of them (create a slow2) to the start of the array (initialized to 0). Both pointers (slow and slow2) are then moved one step at a time until they meet again. The meeting point is the start of the cycle and corresponds to the duplicate number.

### Code:
```
class Solution {
    public int findDuplicate(int[] nums) {
        int slow = 0;
        int fast = 0;
        while (true) {
            slow = nums[slow];
            fast = nums[nums[fast]];
            if (slow == fast) {
                break;
            }
        }
        int slow2 = 0;
        while (true) {
            slow = nums[slow];
            slow2 = nums[slow2];
            if (slow == slow2) {
                return slow;
            }
        }
    }
}
```