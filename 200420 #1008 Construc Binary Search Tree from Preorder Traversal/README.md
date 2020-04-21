# 200418 #64 Minimum Path Sum
Link: https://leetcode.com/problems/minimum-path-sum/

## Description
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

Example:

    Input:
    [
      [1,3,1],
      [1,5,1],
      [4,2,1]
    ]
    Output: 7
    Explanation: Because the path 1→3→1→1→1 minimizes the sum.


## 1<sup>st</sup> trial

### Intuition
Minimum sum of all numbers along its path (Minsum) to specific point A would be the smaller of the (Minsum to the point left to the point A + the number of A) or (Minsum to the point up to the point A + the number of A). This structure reminds me of greedy search. Here I updated the minimum number of specific point from the starting point to the end point iteratively.

### Code
```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        
        collen, rowlen = len(grid), len(grid[0])
        
        for i in range(collen):
            for j in range(rowlen):
                if 0 <= i-1 and 0 <= j-1:
                    tmp = min(grid[i-1][j], grid[i][j-1])
                elif 0 <= i-1:
                    tmp = grid[i-1][j]
                elif 0 <= j-1:
                    tmp = grid[i][j-1]
                else:
                    tmp = 0
                grid[i][j] += tmp
        
        return grid[collen-1][rowlen-1]
```

### Results
**Time complexity**: *O*(n) for single pass of all the elements in the grid.

**Space complexity**: *O*(1) for storing *collen, rowlen, and tmp* (except for the grid, which was previously given).

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200418%20%2364%20Minimum%20Path%20Sum/1st%20trial.PNG)
