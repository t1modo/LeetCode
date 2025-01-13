# 268. Missing Number

### Approach 1:
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

### Approach 2:
To find the missing number in the array, we can leverage the XOR operator (^) in Java. The XOR operation compares the binary representation of two numbers bit by bit, returning 0 for matching bits (both 0 or both 1) and 1 for differing bits (0 and 1 or 1 and 0). A key property of XOR is that it cancels out identical numbers (a ^ a = 0) and any number XORed with 0 remains unchanged (a ^ 0 = a).

### Code:
```
class Solution {
    public int missingNumber(int[] nums) {
        int num = nums.length;
        for (int i = 0; i < nums.length; i++) {
            num ^= nums[i];
            num ^= i;
        }
        return num;
    }
}
```