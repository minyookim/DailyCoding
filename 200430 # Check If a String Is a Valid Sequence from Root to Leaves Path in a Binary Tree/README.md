# 200430 # Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree
Link: https://leetcode.com/problems/check-if-a-string-is-a-valid-sequence-from-root-to-leaves-path-in-a-binary-tree/

## Description
Given a binary tree where each path going from the root to any leaf form a valid sequence, check if a given string is a valid sequence in such binary tree.

We get the given string from the concatenation of an array of integers arr and the concatenation of all values of the nodes along a path results in a sequence in the given binary tree.

**Example1**

    Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,1,0,1]
    Output: true
    Explanation: 
    The path 0 -> 1 -> 0 -> 1 is a valid sequence (green color in the figure). 

    Other valid sequences are: 
    0 -> 1 -> 1 -> 0 
    0 -> 0 -> 0

**Example2**

    Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,0,1]
    Output: false 
    Explanation: The path 0 -> 0 -> 1 does not exist, therefore it is not even a sequence.

**Example3**

    Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,1,1]
    Output: false
    Explanation: The path 0 -> 1 -> 1 is a sequence, but it is not a valid sequence.

## 1<sup>st</sup> trial

### Intuition
I cannot access to my code anymore, since this was the problem that is exposed only to a premium user.

### Code
I cannot access to my code anymore, since this was the problem that is exposed only to a premium user.

### Results
**Time complexity**: *O*(n) for single passing all the possible node.

**Space complexity**: *O*(n) for storing *self.dict*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200430%20%23%20Check%20If%20a%20String%20Is%20a%20Valid%20Sequence%20from%20Root%20to%20Leaves%20Path%20in%20a%20Binary%20Tree/1st%20trial.png)
