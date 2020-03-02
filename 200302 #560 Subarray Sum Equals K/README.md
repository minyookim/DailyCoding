# 200302 #560 Subarray Sum Equals K
Link: https://leetcode.com/problems/subarray-sum-equals-k/

## Description
Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

Example 1:
    Input: nums = [1,1,1], k = 2
    Output: 2

Note:
The length of the array is in range [1, 20,000].
The range of numbers in the array is [-1000, 1000] and the range of the integer k is [-1e7, 1e7].

## 1<sup>st</sup> trial

### Intuition
Simply summing every possible subarrays using two pointers (*i*: start index, *j*: end index). Whenever the sum equals the target integer k, increment the *cnt*.

**Time complexity**: *O*(n<sub>3</sub>), since considering every possible subarrays will take O(n^2) and summing step will take O(n).

**Space complexity**: *O*(1) for storing constant variable i, j, and cnt.

'''
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        
        cnt = 0
        for i in range(len(nums)):
            for j in range(len(nums)-i):
                if k == sum(nums[i:i+j+1]):
                    cnt += 1
        return cnt
'''

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200302%20%23560%20Subarray%20Sum%20Equals%20K/1st%20trial%20with%20brute%20force%20algorithm.PNG)

## 2<sup>nd</sup> trial
