# 338. Counting Bits

### Approach:
Initialize an array to store the number of 1 bits for each unique number from 0 to n. As we iterate up we can use Java's built-in method: Integer.bitCount(), to calculate the number of 1 bits. Once that value is computed we can set the array at index i to that value.

### Code:
```
class Solution {
    public int[] countBits(int n) {
        int[] result = new int[n+1];
        int i = 0;
        while (i <= n) {
            result[i] = (Integer.bitCount(i));
            i++;
        }
        return result;
    }
}
```