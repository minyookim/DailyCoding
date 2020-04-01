# 200330 #139 Word Break
Link: https://leetcode.com/problems/word-break/

## Description
Given a **non-empty** string s and a dictionary *wordDict* containing a list of **non-empty** words, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

**Note:**

- The same word in the dictionary may be reused multiple times in the segmentation.
- You may assume the dictionary does not contain duplicate words.


**Example 1:**

    Input: s = "leetcode", wordDict = ["leet", "code"]
    Output: true
    Explanation: Return true because "leetcode" can be segmented as "leet code".

**Example 2:**

    Input: s = "applepenapple", wordDict = ["apple", "pen"]
    Output: true
    Explanation: Return true because "applepenapple" can be segmented as "apple pen apple".
                 Note that you are allowed to reuse a dictionary word.

**Example 3:**

    Input: s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]
    Output: false

## 1<sup>st</sup> trial

### Intuition
The given problem has optimal substructure property, so it can be solved in dynamic programming (see my solution for the problem #416) with these three steps.

    1. Find the index of every words in *wordDict*. 
    2. Sort them in an increasing order.
    3. If the substring from the start point to the i th point can be made by words in wordDic, then the substring from the start point to the i+ len(***k***) can be made using the word ***k*** that starts from i th point.

### Code
```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        
        idxlst = []
        
        for i in wordDict:
            idx, j = [], 0
            while j < len(s):
                tmp = s.find(i,j,len(s))
                if tmp == -1:
                    j += len(s)
                else:
                    idx.append(tmp)
                    j = tmp+1
            for j in idx:
                idxlst.append((j,j+len(i)))
        idxlst.sort()
        
        anslst = [True] + [False]*(len(s))
        
        for (i,j) in idxlst:
            if anslst[i] == True:
                anslst[j] = True
        
        return anslst[-1]
```

### Results
**Time complexity**: *O*(n<sup>2</sup>) for getting index of the every words in wordDic in the worst case.

**Space complexity**: *O*(n<sup>2</sup>) for storing *idxlst* in the worst case.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200330%20%23139%20Word%20Break/1st%20trial.PNG)
