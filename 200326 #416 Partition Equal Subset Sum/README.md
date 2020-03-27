# 200326 #416 Partition Equal Subset Sum
Link: https://leetcode.com/problems/partition-equal-subset-sum/

## Description

Given a non-empty array containing only positive integers, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.

**Note:**

Each of the array element will not exceed 100. The array size will not exceed 200.

**Example 1:**

Input: [1, 5, 11, 5]

Output: true

Explanation: The array can be partitioned as [1, 5, 5] and [11].

**Example 2:**

Input: [1, 2, 3, 5]

Output: false

Explanation: The array cannot be partitioned into equal sum subsets.


## 1<sup>st</sup> trial

### Intuition
This problem asks whether it is possible to find list whose sum equals to 1/2 of sum of the given list. 

    For element a in the given list, if we can make x through summing other elements, we can then make x-a.
    For element b in the given list, if we can make x through summing elements other than a and b, we can then make x-b, and x-a-b.
    ...

As so, we can iterate this for every elements in the given list and check the possibiility of making the target value (half of the sum of the given list).

### Code
```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        
        if (sum(nums) % 2):
            return False
        
        target = sum(nums)//2        
        anslst = [True] + [False]*target
        
        for i in nums:
            for j in range(target, i-1, -1):
                anslst[j] = anslst[j] or anslst[j-i]
        
        return anslst[-1]
```

### Results
**Time complexity**: *O*(n<sup>2</sup>) for checking every elements in the nums list for the numbers of nums list.

**Space complexity**: *O*(n) for storing *anslst*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200326%20%23416%20Partition%20Equal%20Subset%20Sum/1st%20trial.PNG)
