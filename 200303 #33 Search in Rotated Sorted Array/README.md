# 200303 #33 Search in Rotated Sorted Array
Link: https://leetcode.com/problems/search-in-rotated-sorted-array/

## Description
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

Your algorithm's runtime complexity must be in the order of O(log n).

Example 1:

    Input: nums = [4,5,6,7,0,1,2], target = 0
    Output: 4
    Example 2:


    Input: nums = [4,5,6,7,0,1,2], target = 3
    Output: -1

Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

## 1<sup>st</sup> trial

### Intuition
In order to achieve the runtime complexity of O(log n) in semi-ordered array, I used the binary search (https://en.wikipedia.org/wiki/Binary_search_algorithm) twice: one for searching the pivot point and the other for searching the target.

First loop is for searching the pivot by utilizing binary search. After finding the pivot, I checked whether the value is in the range (nums[pivot] <= target <= nums[r]) and set *l* or *r* variable correspondingly. Then, I performed another binary search to find the target.

### Code
    class Solution:
        def search(self, nums: List[int], target: int) -> int:
            if not nums: return -1
            
            l, r = 0, len(nums)-1
            while l != r: #Find pivot
                m = (l+r)//2
                if nums[m]>nums[r]:
                    l = m+1
                else: r= m

            pivot, l, r = l, 0, len(nums)-1
            if nums[pivot] <= target <= nums[r]:
                l = pivot
            else: r = pivot

            while l <= r: 
                m = (l+r)//2
                if nums[m]>target:
                    r = m-1
                elif nums[m]<target:
                    l = m+1
                else: return m
            return -1

### Results
**Time complexity**: *O*(log n) for the binary search.

**Space complexity**: *O*(1) for storing constant variable l, r, m, and pivot.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200303%20%2333%20Search%20in%20Rotated%20Sorted%20Array/1st%20trial%20with%20binary%20search.PNG)

### Discussions
Binary search algorithm is conceptually simple, yet somewhat tricky to implement at once. Taking care of the details in conditions will be needed.

Although I solved this problem using two while loops, algorithm with one loop may solve this problem if you carefully set the comparison conditions. This may lead to a slightly better runtime performance.
