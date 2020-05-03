# 200427 #221 Maximal Square
Link: https://leetcode.com/problems/maximal-square/

## Description
Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

**Example:**

    Input: 

    1 0 1 0 0
    1 0 1 1 1
    1 1 1 1 1
    1 0 0 1 0

    Output: 4


## 1<sup>st</sup> trial

### Intuition
While searching through every element in the matrix, if the element is "1", update the possible largest area, which include that element by checking the minimum value among the left, upper, and upper left elements. 

### Code
```python
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        
        if not matrix: return 0
        
        tbl = [[0 for i in range(len(matrix[0])+1)] for j in range(len(matrix)+1)]
        ans = 0
        
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                if matrix[i][j] == "1":
                    tbl[i+1][j+1] = min(tbl[i][j], tbl[i+1][j], tbl[i][j+1]) + 1
                    ans = max(ans, tbl[i+1][j+1])
                    
        return ans * ans
```

### Results
**Time complexity**: *O*(n) for single pass of every elements in matrix.

**Space complexity**: *O*(n) for storing approximately n elements in tbl.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200427%20%23221%20Maximal%20Square/1st%20trial.png)
