# 200515 #34 Find First and Last Position of Element in Sorted Array
Link: https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

## Description
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

**Example 1:**

    Input: nums = [5,7,7,8,8,10], target = 8
    Output: [3,4]

**Example 2:**

    Input: nums = [5,7,7,8,8,10], target = 6
    Output: [-1,-1]

## 1<sup>st</sup> trial

### Intuition
Here I used binary search twice to find the leftmost index and rightmost index of the targets.

### Code
```python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        
        start, end = 0, len(nums)
        
        while start < end:
            mid = (start + end) // 2
            if nums[mid] >= target:
                end = mid
            else:
                start = mid + 1
        
        if start == len(nums) or nums[start] != target:
            return [-1, -1]
        
        ans = [start, 0]
        start, end = 0, len(nums)
        
        while start < end:
            mid = (start + end) // 2
            if nums[mid] > target:
                end = mid
            else: start = mid + 1
        ans[1] = start - 1
        
        return ans
```

### Results
**Time complexity**: *O*(log n) for performing binary search twice.

**Space complexity**: *O*(1) for storing *ans, start, end, and mid*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200515%20%2334%20Find%20First%20and%20Last%20Position%20of%20Element%20in%20Sorted%20Array/1st%20trial.png)
