# 200331 #279 Perfect Squares
Link: https://leetcode.com/problems/perfect-squares/

## Description
Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n.

**Example 1:**

    Input: n = 12
    Output: 3 
    Explanation: 12 = 4 + 4 + 4.

**Example 2:**

    Input: n = 13
    Output: 2
    Explanation: 13 = 4 + 9.

## 1<sup>st</sup> trial

### Intuition
The first approach that came to my mind was dynamic programming, but I speculated that there might be some other mathematical regularities. After finding the least number of perfect square numbers, from 1 to 35, I observed that every integers can be expressed with at least 4 sum of perfect square numbers. I googled the internet and I found the regarding theorems as follows:

**Lagrange's four-square theorem**

    Every natural number can be represented as the sum of four integer squares.
    
    Ref: https://en.wikipedia.org/wiki/Lagrange%27s_four-square_theorem


**Legendre's three-square theorem**

    A natural number can be represented as the sum of three squares of integers ***n = x<sup>2</sup>+y<sup>2</sup>+z<sup>2</sup>}***
    if and only if n is not of the form ***n = 4<sup>a</sup>(8b+7)*** for nonnegative integers a and b.
    
    Ref: https://en.wikipedia.org/wiki/Legendre%27s_three-square_theorem

**Two-square theorem**

    An integer greater than one can be written as a sum of two squares if and only if its prime decomposition contains no prime congruent to ***3 modulo 4*** raised to an odd power.
    
    Ref: https://en.wikipedia.org/wiki/Sum_of_two_squares_theorem

Here, I utilized these theorems to solve this question efficiently.

### Code
```python
class Solution:
    def numSquares(self, n: int) -> int:
        
        import math
        sqrt = math.sqrt(n)
        
        if sqrt.is_integer():
            return 1
        
        for i in range(1,int(sqrt)+1):
            if math.sqrt(n - i*i).is_integer():
                return 2
        
        while (n/4).is_integer():
            n= n/4
        if n%8 == 7:
            return 4
        else:
            return 3
```

### Results
**Time complexity**: *O*(log n) for the loop that returns 2.

**Space complexity**: *O*(1) for storing *sqrt and n*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200331%20%23279%20Perfect%20Squares/1st%20trial.PNG)
