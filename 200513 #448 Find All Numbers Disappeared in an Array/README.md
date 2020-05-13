# 200513 #448 Find All Numbers Disappeared in an Array
Link: https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/

## Description
Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

    Example:

    Input:
    [4,3,2,7,8,2,3,1]

    Output:
    [5,6]


## 1<sup>st</sup> trial

### Intuition
After making a set of nums, if an element (that spans from 1 to n) is not in the set, append the element in the answer array.

### Code
```python
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        
        lenN, ans, nums = len(nums), [], set(nums)
        
        for i in range(1,lenN+1):
            if i not in nums:
                ans.append(i)
        
        return ans
```

### Results
**Time complexity**: *O*(n) for single pass of every numbers from 1 to n.

**Space complexity**: *O*(1) for storing *lenN* (except the returned list *ans*).

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200513%20%23448%20Find%20All%20Numbers%20Disappeared%20in%20an%20Array/1st%20trial.png)
