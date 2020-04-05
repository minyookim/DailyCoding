# 200404 #283 Move Zeroes
Link: https://leetcode.com/problems/move-zeroes/

## Description
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

**Example:**

    Input: [0,1,0,3,12]
    Output: [1,3,12,0,0]

**Note:**

You must do this in-place without making a copy of the array.
Minimize the total number of operations.

## 1<sup>st</sup> trial

### Intuition
While iterating through nums, if the current element of the nums array is zero, pop out the element and append 0 to the end of the nums array. This will move all the zeroes while preserving the relative orders of non-zero elements.

### Code
```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        
        i, j = 0, len(nums)
        while i<j:
            if nums[i]==0:
                nums.pop(i)
                nums.append(0)
                j -=1
            else:
                i+= 1
```

### Results
**Time complexity**: *O*(n) for iterating once for every elements in nums array.

**Space complexity**: *O*(1) for storing *i and j*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200404%20%23283%20Move%20Zeroes/1st%20trial.PNG)
