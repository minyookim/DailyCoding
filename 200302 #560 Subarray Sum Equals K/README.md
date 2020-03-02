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

### Code
    class Solution:
        def subarraySum(self, nums: List[int], k: int) -> int:
            cnt = 0
            for i in range(len(nums)):
                for j in range(len(nums)-i):
                    if k == sum(nums[i:i+j+1]):
                        cnt += 1
            return cnt

### Results
**Time complexity**: *O*(n<sub>3</sub>), since considering every possible subarrays will take O(n^2) and summing step will take O(n).

**Space complexity**: *O*(1) for storing constant variable i, j, and cnt.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200302%20%23560%20Subarray%20Sum%20Equals%20K/1st%20trial%20with%20brute%20force%20algorithm.PNG)

## 2<sup>nd</sup> trial

### Intuition
The need for time complexity improvement can be easily met by using cummulative sum (*subsum*), instead of using two pointers. This will yield the summation step to take O(1) instead of O(n).

### Code
    class Solution:
        def subarraySum(self, nums: List[int], k: int) -> int:

            ans = 0
            for i in range(len(nums)):
                subsum, cnt = 0, 0
                while i+cnt < len(nums):
                    subsum += nums[i+cnt]
                    if k == subsum:
                        ans += 1
                    cnt += 1
            return ans

### Results
**Time complexity**: *O*(n<sub>2/sub>), since considering every possible subarrays will take O(n^2). Note that summing step does **not** take O(n).
    
**Space complexity**: *O*(1) for storing constant variable i, subsum, and cnt.

![2nd trial](https://github.com/minyookim/DailyCoding/blob/master/200302%20%23560%20Subarray%20Sum%20Equals%20K/2nd%20trial%20with%20cummulative%20summation.PNG)

## 3<sup>rd</sup> trial

### Intuition
Summation of continuous subarrays can be viewed as the subtraction of two different ***cumulative subarrays***, both starting from the index 0. For instance, let's consider the string [a b c d e f g] as an input. Substring [d e f] can be considered as [a b c d e f] - [a b c] and sub string [c] can be viewed as [a b c] - [a b]. Note that the *second term* (e.g. [a b]) always be the substring of the *first term* (e.g. [a b c]).

Therefore, if we store the summation value of *cumulative subarrays* in dictionary where the key is sum of *cumulative subarrays* and the value is the frequency of that sum, we can achieve the time performance of O(n). To be specific, while we iterate a loop for length of input string times, calculate *subsum* (the sum of *cumulative subarrays*), find whether "the *subsum* minus target *k*" is in the dictionary, and increment the *ans* only when the value exists in the dictionary. Here, *subsum* corresponds to the sum of *first term* and "the *subsum* minus target *k*" corresponds to the sum of *second term*. After this, store the *subsum* in the dictionary *subsumArray*.

### Code
    class Solution:
        def subarraySum(self, nums: List[int], k: int) -> int:

            ans, subsum, subsumArray = 0, 0, {0:1}
            for i in range(len(nums)):
                subsum += nums[i]
                if subsum-k in subsumArray:
                    ans += subsumArray[subsum-k]
                if subsum in subsumArray:
                    subsumArray[subsum] +=1
                else:
                    subsumArray[subsum] = 1
            return ans
            
### Results
**Time complexity**: *O*(n).
    
**Space complexity**: *O*(n) for storing the dictionary.

![3rd trial](https://github.com/minyookim/DailyCoding/blob/master/200302%20%23560%20Subarray%20Sum%20Equals%20K/3rd%20trial%20with%20dictionary.PNG)
