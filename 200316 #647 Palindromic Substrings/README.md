# 200316 #647 Palindromic Substring
Link: https://leetcode.com/problems/palindromic-substrings/

## Description
Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.

**Example 1:**

    Input: "abc"
    Output: 3
    Explanation: Three palindromic strings: "a", "b", "c".

**Example 2:**

    Input: "aaa"
    Output: 6
    Explanation: Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
 

**Note:**

The input string length won't exceed 1000.

## 1<sup>st</sup> trial

### Intuition
Here I used the algorihm that finds and utilizes the seeds for the palindromic substrings. First, I listed the seeds with length 1 or 2. For example, in a word 'banana', the seed will be ['a', 'n', 'a', 'n']. The substrings with 2 same letters can be seeds, such as 
'mm' in 'common'.

Then, expand the seeds by checking whether the s[a-1] is same as s[b+1] where (a, b) is the index of the first and last letter of palindromic seeds.

### Code
```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        
        # Initialization
        if len(s)<2:
            return len(s)
        idx =[]
        
        # Seed for palindromic substrings
        for i in range(1,len(s)-1): #palindromic strings with length = 1
            idx.append((i,i))
        
        for i in range(1, len(s)): #palindromic strings with length = 2
            if s[i-1] == s[i]:
                idx.append((i-1,i))
        
        # Counting expanded palindromic substrings from the seeds
        ans = len(idx)+2 #for (0,0) and (len(s)-1, len(s))
        
        while idx:
            (i,j)=idx.pop()
            if i>0 and j<len(s)-1:
                if s[i-1] == s[j+1]:
                    ans += 1
                    idx.append((i-1,j+1))
        
        return ans
```

### Results
**Time complexity**: *O*(n<sup>2</sup>) for checking the expanding O(n) seeds. 

**Space complexity**: *O*(n) for storing *idx*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200316%20%23647%20Palindromic%20Substrings/1st%20trial.PNG)

## Discussions
I implemented the seed algorithm, which can be used in multiple other problems I solved.

While I'm working on this problem, I found the Manacher's Algorithm can solve this question within O(n) runtime. Implementing this will lead to improvement in runtime performance.
