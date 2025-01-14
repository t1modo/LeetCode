# 128. Longest Consecutive Sequence

### Approach:
We can use a HashSet to efficiently find the longest consecutive sequence in an unsorted array. First, add all elements from the array into the set. This ensures uniqueness which is crucial for optimizing performance. Then iterate over each element in the set, checking if it can be the starting point of a consecutive sequence. Specifically, we checks whether the current number minus one is present in the set. If not, the current number is the start of a new sequence. From there, we can use a while loop to find how far the consecutive sequence extends by checking subsequent numbers (num + length). The length of this sequence is tracked and compared with the longest sequence found so far. After examining all elements, the method returns the length of the longest consecutive sequence.

### Code:
```
class Solution {
    public int longestConsecutive(int[] nums) {
        int longest = 0;
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }
        for (int num : set) {
            int length = 1;
            if (!(set.contains(num - 1))) {
                while (set.contains(num + length)) {
                    length++;
                }
                longest = Math.max(longest, length);
            }
        }
        return longest;
    }
}
```