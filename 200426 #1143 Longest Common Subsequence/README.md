# 200426 #1143 Longest Common Subsequence
Link: https://leetcode.com/problems/longest-common-subsequence/

## Description
Given two strings text1 and text2, return the length of their longest common subsequence.

A subsequence of a string is a new string generated from the original string with some characters(can be none) deleted without changing the relative order of the remaining characters. (eg, "ace" is a subsequence of "abcde" while "aec" is not). A common subsequence of two strings is a subsequence that is common to both strings.

If there is no common subsequence, return 0.

**Example 1:**

    Input: text1 = "abcde", text2 = "ace" 
    Output: 3  
    Explanation: The longest common subsequence is "ace" and its length is 3.

**Example 2:**

    Input: text1 = "abc", text2 = "abc"
    Output: 3
    Explanation: The longest common subsequence is "abc" and its length is 3.

**Example 3:**

    Input: text1 = "abc", text2 = "def"
    Output: 0
    Explanation: There is no such common subsequence, so the result is 0.


**Constraints:**

    1 <= text1.length <= 1000
    1 <= text2.length <= 1000
    The input strings consist of lowercase English characters only.


## 1<sup>st</sup> trial

### Intuition
This problem holds an optimal substructure property. If both sequences start with same letter, then longest common subsequence (LCS) will contain the first letter. If not, removing the letter from one sequence will still yield the same result. Generally speaking,

LCS(Xi~m, Yi~n) = 
1) Xi + LCS(Xi+1~m, Yi+1~m) (if Xi == Yi)
2) max(LCS(Xi+1~m, Yi~m), LCS(Xi~m, Yi+1~m)) (if Xi != Yi)

I used a table for dynamic programming.

### Code
```python
class Solution:
    def longestCommonSubsequence(self, text1: str, text2: str) -> int:
        
        tbl = [[0 for j in range(len(text2)+1)] for i in range(len(text1)+1)]
        
        for i in range(len(text1)):
            for j in range(len(text2)):
                if text1[i] == text2[j]:
                    tbl[i+1][j+1] = tbl[i][j] + 1
                else:
                    tbl[i+1][j+1] = max(tbl[i][j+1], tbl[i+1][j])
        
        return tbl[-1][-1]
```

### Results
**Time complexity**: *O*(nm) for moving over n X m elements in the *tbl*.

**Space complexity**: *O*(nm) for storing n X m elements in the *tbl*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200426%20%231143%20Longest%20Common%20Subsequence/1st%20trial.png)
