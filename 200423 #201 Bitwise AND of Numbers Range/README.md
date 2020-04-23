# 200423 #201 Bitwise AND of Numbers Range
Link: https://leetcode.com/problems/bitwise-and-of-numbers-range/

## Description
Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

Example 1:

    Input: [5,7]
    Output: 4

Example 2:

    Input: [0,1]
    Output: 0

## 1<sup>st</sup> trial

### Intuition
If m and n are not same in the larger bits, then the bitwise AND of all numbers in the range from m to n won't be same in the smaller bits. Therefore, check whether m and n are same while removing the lower bits, and if so, return the bits that m and n have in common would return the answer.

### Code
```python
class Solution:
    def rangeBitwiseAnd(self, m: int, n: int) -> int:        
        cnt = 0
        
        while m != n:
            cnt += 1
            m >>= 1
            n >>= 1
            
        return m << cnt
```

### Results
**Time complexity**: *O*(logn) for single pass of all bit digits.

**Space complexity**: *O*(1) for storing *cnt*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200423%20%23201%20Bitwise%20AND%20of%20Numbers%20Range/1st%20trial.png)
