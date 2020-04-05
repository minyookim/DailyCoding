# 200405 #122 Best Time to Buy and Sell Stock II
Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/

## Description
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

**Note:** You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

**Example 1:**

    Input: [7,1,5,3,6,4]
    Output: 7
    Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
                 Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.

**Example 2:**

    Input: [1,2,3,4,5]
    Output: 4
    Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
                 Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
                 engaging multiple transactions at the same time. You must sell before buying again.
**Example 3:**

    Input: [7,6,4,3,1]
    Output: 0
    Explanation: In this case, no transaction is done, i.e. max profit = 0.

## 1<sup>st</sup> trial

### Intuition
For the maximum profit, you should get every possible profit that can be made. Summing all the possible profit between the days and the next days will yield the answer.

### Code
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        
        ans = 0
        for i in range(0,len(prices)-1):
            if prices[i]<prices[i+1]:
                ans += prices[i+1]-prices[i]
        
        return ans
```

### Results
**Time complexity**: *O*(n) for single pass.

**Space complexity**: *O*(1) for storing *ans*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200405%20%23122%20Best%20Time%20to%20Buy%20and%20Sell%20Stock%20II/1st%20trial.PNG)
