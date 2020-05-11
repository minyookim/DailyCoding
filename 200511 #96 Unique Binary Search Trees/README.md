# 200511 #96 Unique Binary Search Trees
Link: https://leetcode.com/problems/lru-cache/

## Description
Given n, how many structurally unique BST's (binary search trees) that store values 1 ... n?

**Example:**

    Input: 3
    Output: 5
    Explanation:
    Given n = 3, there are a total of 5 unique BST's:

       1         3     3      2      1
        \       /     /      / \      \
         3     2     1      1   3      2
        /     /       \                 \
       2     1         2                 3

## 1<sup>st</sup> trial

### Intuition
Structurally different BSTs originate from the sequence of the inputs and there are n! numbers of the sequences for n integers, so you may think that the regularities underlying the answer may be expressed with factorials. 

If you put n from 1 to 6, the answer will be 1, 2, 5, 14, 42, 132, which are Catalan numbers from combinatorics. Catalan numbers can be calculated using the expression (2n)!/n!(n+1)!

### Code
```python
import math

class Solution:
    def numTrees(self, n: int) -> int:
        
        ans = int(math.factorial(2*n)/(math.factorial(n)*math.factorial(n+1)))
        return ans
```

### Results
**Time complexity**: *O*(n) for calculating math.factorial?

**Space complexity**: *O*(1) for storing *ans*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200511%20%2396%20Unique%20Binary%20Search%20Trees/1st%20trial.png)

### Discussion
Memoization methods with global variable may help reduce the time spent on the calculation of the factorials.
