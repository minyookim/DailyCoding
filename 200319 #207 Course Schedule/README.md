# 200319 #207 Course Schedule
Link: https://leetcode.com/problems/course-schedule/

## Description
There are a total of numCourses courses you have to take, labeled from 0 to numCourses-1.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: [0,1]

Given the total number of courses and a list of prerequisite pairs, is it possible for you to finish all courses?

**Example 1:**

    Input: numCourses = 2, prerequisites = [[1,0]]
    Output: true
    Explanation: There are a total of 2 courses to take. 
                 To take course 1 you should have finished course 0. So it is possible.

**Example 2:**

    Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
    Output: false
    Explanation: There are a total of 2 courses to take. 
                 To take course 1 you should have finished course 0, and to take course 0 you should
                 also have finished course 1. So it is impossible.
 

**Constraints:**

The input prerequisites is a graph represented by a list of edges, not adjacency matrices. Read more about how a graph is represented.
You may assume that there are no duplicate edges in the input prerequisites.
1 <= numCourses <= 10^5

## 1<sup>st</sup> trial

### Intuition
Prerequisites have direction. Prerequisite pair [0, 1] means you should have finished course 1 before you take course 0, but not vice versa. This property reminds me of directed graph. Then, this question transforms into the question to find whether there is a cycle in the directed graph. There are two well-known algorithms to search all the elements in the graph: Breadth-first search (BFS) and depth-first search (DFS). You can solve this in either way, but I chose to implement BFS since it gives better runtime performance.

### Code
```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        
        # Make a tree
        inDegree = {i: 0 for i in range(numCourses)}
        graph = {i: [] for i in range(numCourses)}
        
        for [a,b] in prerequisites:
            inDegree[b] += 1
            graph[a].append(b)
        
        queue = []
        
        for i in inDegree:
            if inDegree[i] == 0:
                queue.append(i)
        
        while queue:
            node = queue.pop(0)
            numCourses -= 1
            for i in graph[node]:
                inDegree[i] -= 1
                if inDegree[i] == 0:
                    queue.append(i)
                    
        return not numCourses
```

### Results
**Time complexity**: *O*(n+e) in a sense that n means numCourses and e means number of prerequisites.

**Space complexity**: *O*(n+e) for storing *graph*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200319%20%23207%20Course%20Schedule/1st%20trial.PNG)
