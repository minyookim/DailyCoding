# 200311 #5 Longest Palindromic Substring
Link: https://leetcode.com/problems/longest-palindromic-substring/

## Description
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

**Example 1:**

    Input: "babad"
    Output: "bab"
    Note: "aba" is also a valid answer.

**Example 2:**

    Input: "cbbd"
    Output: "bb"

## 1<sup>st</sup> trial

### Intuition
Perhaps the easiest way to solve this question may be brute-force algorithm, which scans all the substrings and return the longest palindromic substring. Here, two pointers *i* and *j* indicates the start and end index of the substring. Using two pointers, make *subs* and *rev*, the reverse of *subs*. Then, check the palindromicity by examining whether the *subs* eqauls *rev*. If so and the *subs* is longer than previous palindromic substring, update the *ans*.

### Code
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        
        ans = ''
        
        for i in range(len(s)):
            for j in range(len(s)-i+1):
                subs = s[i:i+j]
                rev = subs[::-1]
                
                if subs == rev:
                    if len(subs)>len(ans):
                        ans = subs
        
        return ans
```

### Results
**Time complexity**: *O*(n<sup>3</sup>) for checking the O(n<sup>2</sup>) substrings. 

**Space complexity**: *O*(n) for storing *subs* and *rev*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200311%20%235%20Longest%20Palindromic%20Substring/1st%20trial.PNG)

## Discussions
Initially, I thought that this would exceed time limit, but it worked. However, due to the poor runtime performance, I should come up with better algorithms. 

One possible idea is using seeds, which I will implement and discuss it on weekends.
