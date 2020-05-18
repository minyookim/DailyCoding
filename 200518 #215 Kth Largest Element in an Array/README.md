# 200518 #215 Kth Largest Element in an Array
Link: https://leetcode.com/problems/kth-largest-element-in-an-array/

## Description
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

**Example 1:**

    Input: [3,2,1,5,6,4] and k = 2
    Output: 5

**Example 2:**

    Input: [3,2,3,1,2,4,5,5,6] and k = 4
    Output: 4

**Note:**
You may assume k is always valid, 1 ≤ k ≤ array's length.

## 1<sup>st</sup> trial

### Intuition
Perhaps the easiest solution may be the solution that first sort the array and return the k-th element.

### Code
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        nums.sort()        
        return nums[-k]
```

### Results
**Time complexity**: *O*(nlogn) for sorting the array.

**Space complexity**: I didn't use any extra memories.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200518%20%23215%20Kth%20Largest%20Element%20in%20an%20Array/1st%20trial.png)
