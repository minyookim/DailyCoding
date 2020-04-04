# 200403 #53 Maximum Subarray
Link: https://leetcode.com/problems/maximum-subarray/

## Description
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

**Example:**

    Input: [-2,1,-3,4,-1,2,1,-5,4],
    Output: 6
    Explanation: [4,-1,2,1] has the largest sum = 6.

**Follow up:**

If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

## 1<sup>st</sup> trial

### Intuition
Sum of the maximum subarray can be viewed as maximum values among the subtraction of two cumulative sums (sums from the 1st index, cumsum). While iterating every element, update the minimum value of cumsums and subtract the minimum cumsum with the current cumsum. Lastly, update the sum of the maximum subarray by comparing the previous sum of the maximum subarray with current one. This will yield the answer.

### Code
```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
    
        minsum, cumsum, ans = 0, 0, float('-inf')
        
        for i in nums:
            minsum = min(minsum, cumsum)
            cumsum += i
            ans = max(ans, cumsum - minsum)
        
        return ans
```

### Results
**Time complexity**: *O*(n) for iterating every elements to get *minsum*, *cumsum*, and *ans* values.

**Space complexity**: *O*(n) for storing *minsum, cumsum, ans*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200403%20%2353%20Maximum%20Subarray/1st%20trial.PNG)
