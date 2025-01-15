# 5. Longest Palindromic Substring

### Approach:
We can solve this problem by expanding around possible centers of palindromes. For each index i in the string, two potential palindromes are checked: one with i as the center (odd-length palindrome) and one with i and i+1 as the center (even-length palindrome). For each center, the algorithm expands outward symmetrically, checking whether characters at the left and right pointers match. If they do, it continues expanding the pointers outward until the characters no longer match or the boundaries of the string are reached. During this process, the longest palindrome found so far is tracked. After traversing the entire string, we can return the longest palindromic substring.

### Code:
```
class Solution {
    public String longestPalindrome(String s) {
        String longest = "";
        int length = 0;
        for (int i = 0; i < s.length(); i++) {
            int l = i;
            int r = i;
            while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
                if (r - l + 1 > length) {
                    longest = s.substring(l, r+1);
                    length = r - l + 1;
                }
                l--;
                r++;
            }
            l = i;
            r = i+1;
            while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
                if (r - l + 1 > length) {
                    longest = s.substring(l, r+1);
                    length = r - l + 1;
                }
                l--;
                r++;
            }
        }
        return longest;
    }
}
```