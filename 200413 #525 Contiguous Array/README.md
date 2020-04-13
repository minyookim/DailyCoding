# 200413 #525 Contiguous Array
Link: https://leetcode.com/problems/contiguous-array/

## Description
Given a binary array, find the maximum length of a contiguous subarray with equal number of 0 and 1.

**Example 1:**

    Input: [0,1]
    Output: 2
    Explanation: [0, 1] is the longest contiguous subarray with equal number of 0 and 1.

**Example 2:**

    Input: [0,1,0]
    Output: 2
    Explanation: [0, 1] (or [1, 0]) is a longest contiguous subarray with equal number of 0 and 1.

**Note:** The length of the given binary array will not exceed 50,000.

## 1<sup>st</sup> trial

### Intuition
While updating the "relative" numbers of zeroes compared to ones, store the relative number in the dictionary where the value is an index. Then, find whether the same number is in the dictionary. If so, it means that there was cumulative list (a list from index 0 to i) and if we substract the two lists (the current list and the list that was in the dictionary), we can get the length of the contiguous subarray with equal number of 0 and 1.

### Code
```python
class Solution:
    def findMaxLength(self, nums: List[int]) -> int:
        
        ans, cumdict, zeroes = 0, {0:-1}, 0
        
        for i in range(len(nums)):
            if nums[i]==0:
                zeroes += 1
            elif nums[i]==1:
                zeroes -= 1
            if zeroes in cumdict:
                ans = max(ans,i-cumdict[zeroes])
            if not zeroes in cumdict:
                cumdict[zeroes] = i
        return ans
```

### Results
**Time complexity**: *O*(n) for single pass.

**Space complexity**: *O*(n) for storing the dictionary *cumdict*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200413%20%23525%20Contiguous%20Array/1st%20trial.PNG)
