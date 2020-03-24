# 200323 #98 Validate Binary Search Tree
Link: https://leetcode.com/problems/validate-binary-search-tree/

## Description
Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.
 

**Example 1:**

        2
       / \
      1   3

    Input: [2,1,3]
    Output: true

**Example 2:**

        5
       / \
      1   4
         / \
        3   6

    Input: [5,1,4,null,null,3,6]
    Output: false
    Explanation: The root node's value is 5 but its right child's value is 4.

## 1<sup>st</sup> trial

### Intuition
Binary search tree should obey these two rules:

    The left subtree of a node contains only nodes with keys less than the node's key.
    The right subtree of a node contains only nodes with keys greater than the node's key.

Importantly, this rule means not only the left child node is less than the parent node, but also means all the nodes in the left subtreee is less than the parent node. Therefore, checking not only the direct parent, but also the grander parents, is mandatory.

To solve this question, the algorithm should check every nodes in the binary search tree, which can be implemented by either recursively or iteratively. Here I used iteration to check every node.

### Code
```python
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        
        if not root:
            return True
        
        nodelist = [(root, float('-inf'),float('inf'))]
        
        while nodelist:
            node, low, high = nodelist.pop(0)
            if node.left:
                if low >= node.left.val or node.val <= node.left.val:
                    return False
                nodelist.append((node.left, low, node.val))
            if node.right:
                if high <= node.right.val or node.val >= node.right.val:
                    return False
                nodelist.append((node.right, node.val, high))
        return True
```

### Results
**Time complexity**: *O*(n) for every nodes.

**Space complexity**: *O*(n) for storing *nodelist*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200323%20%2398%20Validate%20Binary%20Search%20Tree/1st%20trial.PNG)
