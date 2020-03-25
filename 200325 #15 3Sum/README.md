# 200325 #15 3Sum
Link: https://leetcode.com/problems/3sum/

## Description
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

**Note:**

The solution set must not contain duplicate triplets.

**Example:**

    Given array nums = [-1, 0, 1, 2, -1, -4],

    A solution set is:
    [
      [-1, 0, 1],
      [-1, -1, 2]
    ]

## 1<sup>st</sup> trial

### Intuition
Here I used two pointers to look through every pair of elements in the list and dictionary to keep every element and its frequency.

Then, the algorithm finds whether the negative of summation of the two values that are designated by two pointers are in the dictionary. If so, add to the list. Please note that I used several if-conditions to process exceptions.

Lastly, this algorithm results in duplicated solutions, so removing the duplicates is necessary. I implemented this with sorting algorithm. 

### Code
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        from collections import Counter
        import itertools
        
        anslst, numlst = [], Counter(nums)
        
        #get solutions using dictionary
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                if j == i+1 or nums[j-1] != nums[j]:
                    k = -(nums[i] + nums[j]) 
                    if numlst[k]:
                        if (nums[i] != k) and (nums[j] != k):
                            anslst.append([nums[i], nums[j], k])
                        else:
                            if nums[i] == 0 and numlst[k] >= 3:
                                anslst.append([nums[i], nums[j], k])
                            elif (nums[i] != 0) and nums[i] == k and numlst[k]>=2:
                                anslst.append([nums[i], nums[j], k])
                            elif (nums[j] != 0) and nums[j] == k and numlst[k]>=2:
                                anslst.append([nums[i], nums[j], k])
        
        #remove duplicates
        anslst = [anslst[i] for i in range(len(anslst)) if i == 0 or anslst[i] != anslst[i-1]]
        
        for i in range(len(anslst)): 
            anslst[i].sort()
        anslst.sort()
        
        ans = [anslst[i] for i in range(len(anslst)) if i == 0 or anslst[i] != anslst[i-1]]
        
        return ans
```

### Results
**Time complexity**: *O*(n<sup>2</sup>) for checking every two pairs in the list.

**Space complexity**: *O*(n<sup>2</sup>) for storing *anslst*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200324%20%2346%20Permutations/1st%20trial.PNG)

### Discussions
As both the time and space complexity indicate, this algorithm is not efficient to find three elements whose sum equals zero.

It will be better if I look deep into the other algorithms in the Discuss section.
