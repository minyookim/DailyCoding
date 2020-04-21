# 200420 #1008 Construct Binary Search Tree from Preorder Traversal
Link: https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/

## Description
Return the root node of a binary search tree that matches the given preorder traversal.

(Recall that a binary search tree is a binary tree where for every node, any descendant of node.left has a value < node.val, and any descendant of node.right has a value > node.val.  Also recall that a preorder traversal displays the value of the node first, then traverses node.left, then traverses node.right.)

**Example 1:**

    Input: [8,5,1,7,10,12]
    Output: [8,5,10,1,7,null,12]

**Note:**

1 <= preorder.length <= 100
The values of preorder are distinct.

## 1<sup>st</sup> trial

### Intuition
Here I first built the insert function to insert the values in the binary search tree. Then, for all the elements in preorder list, insert the element in the tree.

### Code
```python
class Solution:
    def bstFromPreorder(self, preorder: List[int]) -> TreeNode:
        
        def insert(val, node):
            j= True
            while j:
                if node.val > val:
                    if not node.left:
                        node.left = TreeNode(val)
                        j = False
                    else:
                        node = node.left
                else:
                    if not node.right:
                        node.right = TreeNode(val)
                        j = False
                    else:
                        node = node.right
        
        if not preorder:
            return None
        
        root = TreeNode(preorder.pop(0))
                                
        ans = root       
        for i in range(len(preorder)):
            ans = root
            insert(preorder[i], ans)
        
        return ans
```

### Results
**Time complexity**: *O*(n) for single pass of all the elements in preorder.

**Space complexity**: *O*(n) for storing *ans, root*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200420%20%231008%20Construc%20Binary%20Search%20Tree%20from%20Preorder%20Traversal/1st%20trial.PNG)
