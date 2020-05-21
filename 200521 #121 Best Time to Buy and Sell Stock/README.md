# 200521 #121 Best Time to Buy and Sell Stock
Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

## Description
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

**Example 1:**

    Input: [7,1,5,3,6,4]
    Output: 5
    Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
                 Not 7-1 = 6, as selling price needs to be larger than buying price.

**Example 2:**

    Input: [7,6,4,3,1]
    Output: 0
    Explanation: In this case, no transaction is done, i.e. max profit = 0.

## 1<sup>st</sup> trial

### Intuition
If the current value is less than the current minimum value, update the minimum value. If not, calculate the difference between the current value and minimum number and compare the difference with previous max profit stored in *ans*.

### Code
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        ans, minval = 0, float('inf')
        
        for i in prices:
            if i < minval:
                minval = i
            elif i - minval > ans:
                ans = i - minval
        
        return ans
```

### Results
**Time complexity**: *O*(n) for single pass.

**Space complexity**: *O*(1) for storing *ans, minval*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200521%20%23121%20Best%20Time%20to%20Buy%20and%20Sell%20Stock/1st%20trial.png)
