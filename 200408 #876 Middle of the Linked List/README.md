# 200406 #49 Group Anagrams
Link: https://leetcode.com/problems/group-anagrams/

## Description
Given an array of strings, group anagrams together.

**Example:**

    Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
    Output:
    [
      ["ate","eat","tea"],
      ["nat","tan"],
      ["bat"]
    ]

**Note:**

All inputs will be in lowercase.
The order of your output does not matter.

## 1<sup>st</sup> trial

### Intuition
After making the Counter of each string, check whether it was previously generated. 
If so, append the string into the anagram array, and if not, append the string by making new array.

### Code
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        import collections
        
        ans = []
        strcnt = []
        for i in strs:
            tmp = collections.Counter(i)
            if tmp not in strcnt:
                strcnt.append(collections.Counter(i))
                ans.append([i])
            else:
                k= strcnt.index(tmp)
                ans[k].append(i)
        
        return ans
```

### Results
**Time complexity**: *O*(nk) for searching through strcnt array.

**Space complexity**: *O*(n) for storing *strcnt and ans* array.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200406%20%2349%20Group%20Anagrams/1st%20trial.PNG)
