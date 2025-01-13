# 844. Backspace String Compare

### Approach:


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