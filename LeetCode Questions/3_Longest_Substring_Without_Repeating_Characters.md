# 3. Longest Substring Without Repeating Characters

### Approach:
We can use the sliding window technique along with a HashSet to efficiently track the characters in the current window. The l variable represents the left boundary of the window, and r is the right boundary as it traverses the string. As we iterate through the string with r, we check if the character at r is already in the set (indicating a duplicate within the window). If it is, we remove characters from the set starting from the left until the duplicate is removed, incrementing l each time a character is removed. After each modification of the window (adding/removing characters), we calculate the current length of the window (r - l + 1) and update result if this length is greater than the previous maximum found. The approach ensures that we always have a window of unique characters and processes each character only once.

### Code:
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int result = 0;
        int l = 0;
        Set<Character> set = new HashSet<>();
        for (int r = 0; r < s.length(); r++) {
            while (set.contains(s.charAt(r))) {
                set.remove(s.charAt(l));
                l++;
            }
            set.add(s.charAt(r));
            result = Math.max(result, r - l + 1);
        }
        return result;
    }
}
```