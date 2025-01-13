# 1. Two Sum

### Approach:
We can utilize a HashMap to efficiently store and retrieve elements and their indices. Specifically, the HashMap will use the array elements as keys and their corresponding indices as values. As we iterate through the array, for each element, we calculate the difference between the target value and the current element. We then check if this difference exists as a key in the HashMap. If it does, we have found the two indices that sum to the target, and we return them. If not, we add the current element and its index to the HashMap. This process continues until the required pair is identified.

### Code:
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int diff = target - nums[i];
            if (map.containsKey(diff)) {
                return new int[]{map.get(diff), i};
            }
            map.put(nums[i], i);
        }
        return null;
    }
}
```