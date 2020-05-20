# 200520 #62 Unique Paths
Link: https://leetcode.com/problems/unique-paths/

## Description
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

**Example 1:**

    Input: m = 3, n = 2
    Output: 3
    Explanation:
    From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
    1. Right -> Right -> Down
    2. Right -> Down -> Right
    3. Down -> Right -> Right

**Example 2:**

    Input: m = 7, n = 3
    Output: 28

**Constraints:**

1 <= m, n <= 100
It's guaranteed that the answer will be less than or equal to 2 * 10 ^ 9.

## 1<sup>st</sup> trial

### Intuition
After (m+n-2) number of actions, the robot can reach to the destination. In the (m+n-2) number of actions, the robot should move downwards for (m-1) of time and left for (n-1) of time. Thus, this problem can be viewed as the calculation of permutation for (m-1) downs and (n-1) lefts.

### Code
```python
import math

class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        return int(math.factorial(m+n-2)/(math.factorial(m-1)*math.factorial(n-1)))
```

### Results
**Time complexity**: Calculating factorials would determine its big-O notation.

**Space complexity**: I didn't use any extra memories.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200520%20%2362%20Unique%20Paths/1st%20trial.png)
