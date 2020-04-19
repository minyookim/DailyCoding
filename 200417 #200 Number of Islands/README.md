# 200417 #200 Number of Islands
Link: https://leetcode.com/problems/number-of-islands/

## Description
Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

    Input:
    11110
    11010
    11000
    00000

    Output: 1

**Example 2:**

    Input:
    11000
    11000
    00100
    00011

    Output: 3


## 1<sup>st</sup> trial

### Intuition
To visit all the areas, I used breadth-first search algorithm with recursion. If the area is "1" and never visited, I checked whether four adjacent areas are water and if so, I appended the areas into the queue. Repeating this process will reveal all the areas that are connected.  

### Code
```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        
        def bfs(grid,i,j):
            queue = []
            queue.append([i,j])
            while queue:
                [a,b]=queue.pop()
                grid[a][b]=-1 
                if a+1<len(grid) and grid[a+1][b]=="1":
                    queue.append([a+1,b])
                if b+1<len(grid[0]) and grid[a][b+1]=="1":
                    queue.append([a,b+1])
                if b-1>=0 and grid[a][b-1]=="1":
                    queue.append([a,b-1])
                if a-1>=0 and grid[a-1][b]=="1":
                    queue.append([a-1,b])
        
        cnt = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j]=="1":
                    bfs(grid,i,j)
                    cnt+=1
        
        return cnt
```

### Results
**Time complexity**: *O*(n) for single pass of all the elements.

**Space complexity**: *O*(n) for storing *queue*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200417%20%23200%20Number%20of%20Islands/1st%20trial.PNG)
