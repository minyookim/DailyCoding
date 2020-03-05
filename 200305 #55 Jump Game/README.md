# 200305 #55 Jump Game
Link: https://leetcode.com/problems/jump-game/

## Description
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

Example 1:

    Input: [2,3,1,1,4]
    Output: true
    Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
    Example 2:

    Input: [3,2,1,0,4]
    Output: false
    Explanation: You will always arrive at index 3 no matter what. Its maximum
                 jump length is 0, which makes it impossible to reach the last index.

## 1<sup>st</sup> trial

### Intuition
The first thing that came up in my mind was greedy algorithm from the bottom using two pointers. 

Suppose that there are two rabbits. **The first rabbit (called the supply rabbit)** moves one step at a time (pointer i), gathering and providing food for the second rabbit. **The second rabbit (called the scout rabbit)** can move only in the range (pointer j), where the supply rabbit can provide food. **The range** is defined by the amount of gathered food, which corresponds to the *nums[i]*. If the supply rabbit moves farther than the scout rabbit (i>j) or the scout rabbit travels to the end, their journey ends. Whether the scout rabbit saw the end would be the result of their journey. Although this fairy tale seems complicated a bit, the code is quite straightforward.

### Code
```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        i,j=0,0
        while i<=j<len(nums):
            j=max(j,i+nums[i])
            i+=1
        return j>=len(nums)-1
```

### Results
**Time complexity**: *O*(n) for a single pass through the *nums* array.

**Space complexity**: *O*(1) for storing constant *i* and *j*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200305%20%2355%20Jump%20Game/1st%20trial.PNG)

### Discussions
Although I thought this algorithm is fast and simple, its runtime and storage performance was not good enough. However, I cannot think of any better algorithm in a moment.
