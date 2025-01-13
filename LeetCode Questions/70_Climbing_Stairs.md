# 70. Climbing Stairs

### Approach:
The problem can be visualized as a reverse Fibonacci sequence. Starting from the base case at step n, there is exactly one way to reach n (you’re already there). Similarly, for step n − 1, there’s only one way to reach n (a single step). For step n − 2, the number of ways to reach n is the sum of the ways to reach n − 1 and n. This pattern continues as you move down, where the number of ways to reach n from any step is the sum of the ways to reach n from the two subsequent steps.

This bottom-up dynamic programming approach ensures you build the solution iteratively, using previously computed results to efficiently calculate the number of ways for each step.

### Code:
```
class Solution {
    public int climbStairs(int n) {
        int one = 1;
        int two = 1;
        for (int i = n - 1; i > 0; i--) {
            int temp = one;
            one = one + two;
            two = temp;
        }
        return one;
    }
}
```
