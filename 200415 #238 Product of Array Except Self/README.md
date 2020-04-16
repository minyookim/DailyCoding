# 200415 #238 Product of Array Except Self
Link: https://leetcode.com/problems/product-of-array-except-self/

## Description
Given an array nums of n integers where n > 1,  return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

**Example:**

Input:  [1,2,3,4]
Output: [24,12,8,6]

**Constraint:** It's guaranteed that the product of the elements of any prefix or suffix of the array (including the whole array) fits in a 32 bit integer.

**Note:** Please solve it without division and in O(n).

**Follow up:**
Could you solve it with constant space complexity? (The output array does not count as extra space for the purpose of space complexity analysis.)


## 1<sup>st</sup> trial

### Intuition
The i-th element of output array will be the product of all the elements from 1-i-1-th and i+1-end-th elements. By keeping multiplying the l and r variables and update the i-th element of output array with the product of l and r will yield the answer.

### Code
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        
        ans, l, r = [1]*len(nums), 1, 1
        
        for i in range(len(nums)):
            ans[i] *= l
            l *= nums[i]
            ans[-i-1] *= r
            r *= nums[-i-1]
        
        return ans
```

### Results
**Time complexity**: *O*(n) for single pass.

**Space complexity**: *O*(1) for storing *l* and *r* (except for ans array).

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200415%20%23238%20Product%20of%20Array%20Except%20Self/1st%20trial.PNG)
