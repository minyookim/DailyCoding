# 200401 #136 Single Number
Link: https://leetcode.com/problems/single-number/

## Description
Given a non-empty array of integers, every element appears twice except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

    Input: [2,2,1]
    Output: 1

**Example 2:**

    Input: [4,1,2,1,2]
    Output: 4

## 1<sup>st</sup> trial

### Intuition
Every element appears twice except for one that occurs once. If we add all the unique elements from the given list twice and subtract with the sum of list, it will yield the one element that appears once.

### Code
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        
        return 2*sum(set(nums))-(sum(nums))
```

### Results
**Time complexity**: *O*(n) for getting the sum values.

**Space complexity**: *O*(n) for storing *set(nums)*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200401%20%23136%20Single%20Number/1st%20trial.PNG)
