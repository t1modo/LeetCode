# 238. Product of Array Except Self

### Approach:
You can utilize an iterative approach where you traverse the array twice: once from left to right and once from right to left. During the forward iteration, you maintain a running product called the prefix, which represents the product of all numbers to the left of the current index. For each index, you store the prefix value in a new array called "result," and then update the prefix by multiplying it with the current element of the input array, nums[i]. In the backward iteration, you multiply each element in the "result" array by a value called the postfix, which represents the product of all numbers to the right of the current index. As you iterate, you update the postfix by multiplying it with the current element of nums[i]. After completing both iterations, the "result" array will contain the product of all elements in the input array except the one at each respective index, and you simply return the "result" array.

### Code:
```
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int prefix = 1;
        int postfix = 1;
        int[] result = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            result[i] = prefix;
            prefix *= nums[i];
        }
        for (int i = nums.length - 1; i >= 0; i--) {
            result[i] *= postfix;
            postfix *= nums[i];
        }
        return result;
    }
}
```