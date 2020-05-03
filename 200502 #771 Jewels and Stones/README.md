# 200502 #771 Jewels and Stones
Link: https://leetcode.com/problems/jewels-and-stones/

## Description
You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

**Example 1:**

    Input: J = "aA", S = "aAAbbbb"
    Output: 3
**Example 2:**

    Input: J = "z", S = "ZZ"
    Output: 0

## 1<sup>st</sup> trial

### Intuition
For every element in J, store the element in dictionary to enable searching within O(1).
Then, while iterating through every elements in S, if the element is in the dictionary, increment the answer by 1.

### Code
```python
class Solution:
    def numJewelsInStones(self, J: str, S: str) -> int:
        
        ans, jewels = 0, {}
        for i in J:
            jewels[i] = 1
        
        for j in S:
            if j in jewels:
                ans += 1
        
        return ans
```

### Results
**Time complexity**: *O*(n) for single pass.

**Space complexity**: *O*(n) for storing the jewels dictionary.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200502%20%23771%20Jewels%20and%20Stones/1st%20trial.png)
