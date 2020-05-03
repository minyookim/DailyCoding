# 200429 #124 Binary Tree Maximum Path Sum
Link: https://leetcode.com/problems/binary-tree-maximum-path-sum/

## Description
Given a non-empty binary tree, find the maximum path sum.

For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path must contain at least one node and does not need to go through the root.

**Example 1:**

    Input: [1,2,3]

           1
          / \
         2   3

    Output: 6

**Example 2:**

    Input: [-10,9,20,null,null,15,7]

       -10
       / \
      9  20
        /  \
       15   7

    Output: 42


## 1<sup>st</sup> trial

### Intuition
Here, I used almost same algorithm that was used before (https://github.com/minyookim/DailyCoding/tree/master/200411%20%23543%20Diameter%20of%20Binary%20Tree), since the structure of the problem is quite similar between those two.

### Code
```python
class Solution:
    def maxPathSum(self, root: TreeNode) -> int:
        ans = float('-inf')
        
        def calPath(node):
            if not node:
                return 0
            
            nonlocal ans
            pathL = calPath(node.left)
            pathR = calPath(node.right)
            currPath = max(pathL, pathR, 0) + node.val
            candidate = node.val + max(pathL, 0) + max(pathR, 0)
            ans = max(ans, candidate)
            
            return currPath
        
        calPath(root)
        
        return ans
```

### Results
**Time complexity**: *O*(n) for single pass every node.

**Space complexity**: *O*(1) for ans, pathL, pathR, currPath, and candidate.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200429%20%23124%20Binary%20Tree%20Maximum%20Path%20Sum/1st%20trial.png)
