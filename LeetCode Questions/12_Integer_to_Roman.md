# 12. Integer to Roman

### Approach:
We can use a structured approach that involves mapping integer values to their corresponding Roman numeral symbols and iteratively building the resulting string representation. First, we initialize two arrays: one to store the integer values and another to store their corresponding Roman numeral symbols. These arrays are sorted in descending order of values so that we can process the largest values first, ensuring that the Roman numeral representation is constructed correctly.

To efficiently build the resulting string, we utilize a StringBuilder instead of a standard String, as it allows for efficient appending of characters without creating intermediate objects, which can help avoid unnecessary garbage collection. The algorithm proceeds by iterating over the values array. For each value, we check if the input number (num) is greater than or equal to the current value (vals[i]). If this condition is satisfied, it means the current Roman numeral symbol should be included in the result. We append the corresponding symbol from the syms array to the StringBuilder and then reduce the value of num by the current value. This process repeats for the same value as long as num remains greater than or equal to it. Once the current value no longer fits into num, we move to the next smaller value in the array and repeat the process until num becomes zero. Finally, the resulting Roman numeral is obtained by converting the StringBuilder to a string and returning it.

### Code:
```
class Solution {
    public String intToRoman(int num) {
        StringBuilder result = new StringBuilder();
        int[] vals = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        String[] syms = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        for (int i = 0; i < vals.length; i++) {
            while (num >= vals[i]) {
                result.append(syms[i]);
                num -= vals[i];
            }
        }
        return result.toString();
    }
}
```