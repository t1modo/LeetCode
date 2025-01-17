# 217. Contains Duplicate

### Approach:
We can utilize a hashset to store numbers we come across as we iterate through the nums array. Each iteration checks if the set currently contains "num". If the condition is true, we can immediately return true. Otherwise, add the current "num" to the set and continue traversing through the nums array. If we reach the end of nums without returning true, that would indicate that there was no duplicate detected, so we can return false.

### Code:
```
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            if (set.contains(num)) {
                return true;
            }
            set.add(num);
        }
        return false;
    }
}
```