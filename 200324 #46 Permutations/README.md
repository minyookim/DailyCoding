# 200324 #46 Permutations
Link: https://leetcode.com/problems/permutations/

## Description
Given a collection of **distinct** integers, return all possible permutations.

**Example:**

    Input: [1,2,3]
    Output:
    [
      [1,2,3],
      [1,3,2],
      [2,1,3],
      [2,3,1],
      [3,1,2],
      [3,2,1]
    ]

## 1<sup>st</sup> trial

### Intuition
To implement permutation in python is easy - just use Permutation function in itertools!

However, for the sake of learning and practicing algorithms, I implemented Knuth shuffle algorithm, which I had practiced in undergrad. Here is the link I referred to while I was practicing (https://programmers.co.kr/learn/courses/4008/lessons/12836#note). Note that the description is written in Korean. You can easily find other similar implementations by google search Knuth permutation algorithm (e.g. https://stackoverflow.com/questions/25779087/how-to-generate-random-permutations-fast).

### Code
```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        
        ans = [nums[:]]
        c = [0] * len(nums)
        i = 0
        while i < len(nums):
            if c[i] < i:
                if i % 2 == 0:
                    nums[0], nums[i] = nums[i], nums[0]
                else:
                    nums[c[i]], nums[i] = nums[i], nums[c[i]]
                ans.append(nums[:])
                c[i] += 1
                i = 0
            else:
                c[i] = 0
                i += 1
        
        return ans
```

### Results
**Time complexity**: *O*(n!) for making all the permutations.

**Space complexity**: *O*(n!) for storing *ans*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200324%20%2346%20Permutations/1st%20trial.PNG)
