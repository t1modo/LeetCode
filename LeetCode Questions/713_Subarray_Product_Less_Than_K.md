# 713. Subarray Product Less Than K

### Approach:
We can use a two-pointer sliding window approach. The method starts by initializing three variables: l, the left pointer, set to 0; product, the product of elements within the current window, initialized to 1; and result, the count of subarrays, initialized to 0. Use a loop to traverse the array with the right pointer r, multiplying the product by nums[r] on each iteration. If the product exceeds or equals k, the product is adjusted by dividing it by nums[l] and then incrementing l, shrinking the window from the left until the product becomes less than k. After adjusting the window, the number of subarrays with a product less than k is determined by the difference r - l + 1, and this count is added to result. Once the loop finishes, the method returns the total count of subarrays.

### Code:
```
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        int l = 0;
        int product = 1;
        int result = 0;
        for (int r = 0; r < nums.length; r++) {
            product *= nums[r];
            while (l <= r && product >= k) {
                product /= nums[l];
                l++;
            }
            result += r - l + 1;
        }
        return result;
    }
}
```