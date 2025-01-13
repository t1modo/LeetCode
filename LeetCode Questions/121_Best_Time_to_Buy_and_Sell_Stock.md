# 121. Best Time to Buy and Sell Stock

### Approach:
The goal is to maximize profit by buying at a low price and selling at a higher price later. To achieve this, we use a two-pointer approach: the left pointer starts at day 0 (buy day) and the right pointer starts at day 1 (sell day). We also maintain a variable maxProfit initialized to 0 to store the maximum profit. As we iterate through the array with the right pointer moving from left to right, we check if the price at right is greater than the price at left (prices[left] < prices[right]). If so, we calculate the potential profit as prices[right] - prices[left] and update maxProfit if this profit is greater than the current maxProfit. If at any point the right pointer value is less than our left, we update our current left to the value of the right pointer. The process continues until the right pointer reaches the end of the array, at which point we return the value of maxProfit.

### Code:
```
class Solution {
    public int maxProfit(int[] prices) {
        int l = 0;
        int r = 1;
        int maxProfit = 0;
        while (r < prices.length) {
            if (prices[l] < prices[r]) {
                int profit = prices[r] - prices[l];
                maxProfit = Math.max(maxProfit, profit);
            }
            else {
                l = r;
            }
            r++;
        }
        return maxProfit;
    }
}
```