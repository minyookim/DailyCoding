# 200519 #75 Sort Colors
Link: https://leetcode.com/problems/sort-colors/

## Description
Given an array with n objects colored red, white or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

**Note:** You are not suppose to use the library's sort function for this problem.

**Example:**

    Input: [2,0,2,1,1,0]
    Output: [0,0,1,1,2,2]

**Follow up:**

A rather straight forward solution is a two-pass algorithm using counting sort.
First, iterate the array counting number of 0's, 1's, and 2's, then overwrite array with total number of 0's, then 1's and followed by 2's.
Could you come up with a one-pass algorithm using only constant space?

## 1<sup>st</sup> trial

### Intuition
To implement the single-pass algorithm, I used three pointers that indicate the location of insertion. Here, the algorithms checks the value of current element, replace the value, and then move the pointers accordingly

### Code
```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        
        a, b, c = 0, 0, 0
        
        for i in nums:
            
            if i == 0:
                nums[a] = 0
                if a != b:
                    nums[b] = 1
                if b != c:
                    nums[c] = 2
                a += 1
                b += 1
                c += 1
                
            if i == 1:
                nums[b] = 1
                if b != c:
                    nums[c] = 2
                b += 1
                c += 1
                
            if i == 2:
                nums[c] = 2
                c += 1
```

### Results
**Time complexity**: *O*(n) for single pass.

**Space complexity**: *O*(1) for storing *a, b, c*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200519%20%2375%20Sort%20Colors/1st%20trial.png)
