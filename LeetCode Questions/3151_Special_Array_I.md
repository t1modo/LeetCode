# 3151. Special Array I

### Approach:
You can traverse the input array starting at position 1. Then during each iteration, use the modulus operator to check if the current number matches the number before it. In the case that they match we can return false.

### Code:
```
class Solution {
    public boolean isArraySpecial(int[] nums) {
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] % 2 == nums[i-1] % 2) {
                return false;
            }
        }
        return true;
    }
}
```