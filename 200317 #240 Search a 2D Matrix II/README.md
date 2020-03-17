# 200317 #240 Search a 2D Matrix II
Link: https://leetcode.com/problems/search-a-2d-matrix-ii/

## Description
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

    Integers in each row are sorted in ascending from left to right.
    Integers in each column are sorted in ascending from top to bottom.

**Example:**

Consider the following matrix:

    [
      [1,   4,  7, 11, 15],
      [2,   5,  8, 12, 19],
      [3,   6,  9, 16, 22],
      [10, 13, 14, 17, 24],
      [18, 21, 23, 26, 30]
    ]
    
Given target = 5, return true.

Given target = 20, return false.
 

## 1<sup>st</sup> trial

### Intuition
Since integers in each row or column are sorted, we can apply binary search algorithm to each row to search the target. Iterating this to every row will answer the question.

### Code
```python
class Solution:
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        
        if not matrix: return False
        
        numcol = len(matrix[0])
        
        for i in range(numrow):
            l, r = 0, numcol-1
            while l<=r:
                m = (l+r)//2
                if matrix[i][m] < target:
                    l = m+1
                elif matrix[i][m] > target:
                    r = m-1
                else:
                    return True
                        
        return False
```

### Results
**Time complexity**: *O*(n<sup>log m</sup>), where n and m are the number of row and column, respectively. log m for binary search algorithm and n for iterating in every row.

**Space complexity**: *O*(1) for storing *l*, *r*, *m*, *numrow*, and *numcol* .

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200317%20%23240%20Search%20a%202D%20Matrix%20II/1st%20trial.PNG)

## 2<sup>nd</sup> trial

### Intuition
Although the algorithm above can solve the question, it only utilizes one property (Integers in each row are sorted in ascending from left to right), but not the other (Integers in each column are sorted in ascending from top to bottom).

One way to utilize both properties is zig-zag search. The rule is simple:

    1. Start at the rightmost integer in the first row.
    2. If the target exceeds the integer value, every value in the first row is smaller than the target. Therefore, you can skip the first row and move to the second row.
    3. If the rightmost integer in the second row is larger than the target, move left until the value exceeds or is same as the target.
    4. If the value exceeds the target, for the same reason in 2, you can skip to search the other values and move to the next row.
    5. Repeat this algorithm to find the target.
Since integers in each row or column are sorted, we can apply binary search algorithm to each row to search the target. Iterating this to every row will answer the question.

### Code
```python
class Solution:
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        
        if not matrix: return False
        
        row, col = 0, len(matrix[0])-1
        
        while row < len(matrix) and col >=0:
            if matrix[row][col]>target:
                col += -1
            elif matrix[row][col]<target:
                row += 1
            else:
                return True

        return False
```

### Results
**Time complexity**: *O*(n+m) for checking n + m values.

**Space complexity**: *O*(1) for storing *row*, and *col* .

![2nd trial](https://github.com/minyookim/DailyCoding/blob/master/200317%20%23240%20Search%20a%202D%20Matrix%20II/2nd%20trial.PNG)

## Discussions
Although the both algorithm seems similar in terms of space complexity, the below one outperforms the above one.
