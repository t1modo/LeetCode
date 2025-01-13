# 844. Backspace String Compare

### Approach:
You can use a reverse iterative approach to solve this problem. Starting from the end of each string, we process one character at a time, handling valid characters and # backspace characters. Two separate counters, backS and backT, track the number of backspaces for our input strings (s and t). If the current character is #, we increment the respective counter. If it's not #, but the counter (backS or backT) is greater than zero, we decrement the counter and skip the character. Otherwise, we process the character. After processing, if the current valid characters in both strings differ, we return false. Similarly, if one pointer is out of bounds while the other isn't, we return false.

The approach works because # only affects characters to its left, so processing from right to left ensures we finalize characters as we move. If we reach the end without mismatches, we return true.

### Code:
```
class Solution {
    public boolean backspaceCompare(String s, String t) {
        int x = s.length() - 1;
        int y = t.length() - 1;
        int backS = 0;
        int backT = 0;
        while (x >= 0 || y >= 0) {
            while (x >= 0) {
                if (s.charAt(x) == '#') {
                    backS++;
                    x--;
                }
                else if (backS > 0) {
                    backS--;
                    x--;
                }
                else {
                    break;
                }
            }
            while (y >= 0) {
                if (t.charAt(y) == '#') {
                    backT++;
                    y--;
                }
                else if (backT > 0) {
                    backT--;
                    y--;
                }
                else {
                    break;
                }
            }
            if (x >= 0 && y >= 0 && s.charAt(x) != t.charAt(y)) {
                return false;
            }
            if ((x >= 0) != (y >= 0)) {
                return false;
            }
            x--;
            y--;
        }
        return true;
    }
}
```