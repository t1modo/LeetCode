# 136. Single Number

### Approach:
We can utilize the XOR operation. Initialize a variable to store the value of our result (number that only appears once). During each iteration of "nums" we perform XOR on the current value of "result" with the current "num". Once we finish traversing the entire nums array, we can return "result" which is guaranteed the single number.

### Code:
```
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for (int num : nums) {
            result ^= num;
        }
        return result;
    }
}
```