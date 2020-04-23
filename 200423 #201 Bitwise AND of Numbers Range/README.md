# 200421 # Leftmost Column with at Least a One
Link: https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/530/week-3/3306/

## Description
(This problem is an interactive problem.)

A binary matrix means that all elements are 0 or 1. For each individual row of the matrix, this row is sorted in non-decreasing order.

Given a row-sorted binary matrix binaryMatrix, return leftmost column index(0-indexed) with at least a 1 in it. If such index doesn't exist, return -1.

You can't access the Binary Matrix directly.  You may only access the matrix using a BinaryMatrix interface:

BinaryMatrix.get(x, y) returns the element of the matrix at index (x, y) (0-indexed).
BinaryMatrix.dimensions() returns a list of 2 elements [n, m], which means the matrix is n * m.
Submissions making more than 1000 calls to BinaryMatrix.get will be judged Wrong Answer.  Also, any solutions that attempt to circumvent the judge will result in disqualification.

For custom testing purposes you're given the binary matrix mat as input in the following four examples. You will not have access the binary matrix directly.
 

**Example 1:**

    Input: mat = [[0,0],[1,1]]
    Output: 0

**Example 2:**

    Input: mat = [[0,0],[0,1]]
    Output: 1

**Example 3:**

    Input: mat = [[0,0],[0,0]]
    Output: -1

**Example 4:**

    Input: mat = [[0,0,0,1],[0,0,1,1],[0,1,1,1]]
    Output: 1
 
**Constraints:

1 <= mat.length, mat[i].length <= 100
mat[i][j] is either 0 or 1.
mat[i] is sorted in a non-decreasing way.

## 1<sup>st</sup> trial

### Intuition
I used two pointers that designates the x and y value. If the value at the pointers is 0, the values at leftside of the pointer would be all 0, so move one step down. If the value at the pointers is 1, the values at the downside of the pointer would be all 1, so move one step left.

Repeat this until the pointer reaches at the margin of the matrix. If y reaches the margin, then leftmost column that appears at least a 1 would be 0-th column. If x reaches the margin, then the leftmost column that appears at least a 1 would be y+1-th column. If y+1 exceeds the y dimension of the matrix, then no 1 can be found in the matrix- thus, return 0.

### Code
```python
class Solution:
    def leftMostColumnWithOne(self, binaryMatrix: 'BinaryMatrix') -> int:
        
        [m,n] = binaryMatrix.dimensions()
        x, y = 0, n-1
        while x<m and y>=0:
            if binaryMatrix.get(x,y):
                y -=1
            else:
                x += 1
        
        if y == -1:
            return 0
        if x == m:
            if y+1 < n:
                return y+1
            else:
                return -1
```

### Results
**Time complexity**: *O*(n+m) since it passes through n+m elements maximum.

**Space complexity**: *O*(1) for storing *x, y, m, n*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200421%20%23%20Leftmost%20Column%20with%20at%20Least%20a%20One/1st%20trial.PNG)
