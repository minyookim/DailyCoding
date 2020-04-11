# 200411 #543 Diameter of Binary Tree
Link: https://leetcode.com/problems/diameter-of-binary-tree/

## Description
Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

**Example:**

    Given a binary tree
              1
             / \
            2   3
           / \     
          4   5    
    Return 3, which is the length of the path [4,2,1,3] or [5,2,1,3].

**Note:** The length of path between two nodes is represented by the number of edges between them.


## 1<sup>st</sup> trial

### Intuition
Here I utilized depth-first search algorithm using recursion. While searching through all the nodes in the tree, update the nonlocal variable *diameter* by calculating max(current diameter, diameter of the nodes that is calculated by adding diameter of the left node and that of the right node).

### Code
```python
class Solution:
    def diameterOfBinaryTree(self, root: TreeNode) -> int:
        
        diameter = 0
        
        def calDiameter(node):
            if not node:
                return 0
            
            nonlocal diameter
            diameterL = calDiameter(node.left)
            diameterR = calDiameter(node.right)
            diameter = max(diameter, diameterL+diameterR)
            
            return max(diameterL, diameterR) + 1
        
        calDiameter(root)
        
        return diameter
```

### Results
**Time complexity**: *O*(n) for single pass of all the nodes.

**Space complexity**: *O*(1) for storing *diameter, diameterL, diameterR*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200411%20%23543%20Diameter%20of%20Binary%20Tree/1st%20trial.PNG)
