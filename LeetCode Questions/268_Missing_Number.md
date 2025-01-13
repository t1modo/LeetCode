# 268. Missing Number

### Approach:
To find the missing number in the array, initialize a variable result with the value nums.length, since we know exactly one number is missing. Then, iterate through the array from the last index (nums.length - 1) down to 0. In each iteration, add the current index and subtract the current array element nums[i] from result and update result. Once the loop completes, the value in result will be the missing number.

### Code:
```
class Solution {
    public int missingNumber(int[] nums) {
        int result = nums.length;
        for (int i = nums.length-1; i >= 0; i--) {
            result += i - nums[i];
        }
        return result;
    }
}
```