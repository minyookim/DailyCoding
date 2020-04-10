# 200409 #844 Backspace String Compare
Link: https://leetcode.com/problems/backspace-string-compare/

## Description
Given two strings S and T, return if they are equal when both are typed into empty text editors. # means a backspace character.

**Example 1:**

    Input: S = "ab#c", T = "ad#c"
    Output: true
    Explanation: Both S and T become "ac".

**Example 2:**

    Input: S = "ab##", T = "c#d#"
    Output: true
    Explanation: Both S and T become "".

**Example 3:**

    Input: S = "a##c", T = "#a#c"
    Output: true
    Explanation: Both S and T become "c".

**Example 4:**

    Input: S = "a#c", T = "b"
    Output: false
    Explanation: S becomes "c" while T becomes "b".

**Note:**

    1 <= S.length <= 200
    1 <= T.length <= 200
    S and T only contain lowercase letters and '#' characters.

**Follow up:**

    Can you solve it in O(N) time and O(1) space?


## 1<sup>st</sup> trial

### Intuition
While iterating through two strings in reverse, if # letter comes out, increment the counter for # letter. If the counter for # letter is not 0 and the current letter is not #, skip the current letter until the counter for # letter is 0 and the current letter is not #. If both strings reach to the conditions where the current letter is not # and the counter for # letter is 0, check whether the two letters are same.


### Code
```python
class Solution:
    def backspaceCompare(self, S: str, T: str) -> bool:
        
        pointerS, pointerT, cntS, cntT = len(S)-1, len(T)-1, 0, 0
        
        while pointerS >= 0 or pointerT >= 0:
            if pointerS >= 0:
                i = S[pointerS]
            else:
                i = ''
            if pointerT >= 0:
                j = T[pointerT]
            else:
                j = ''
            
            if i == "#":
                cntS += 1
                pointerS -= 1
                continue
                
            if j == "#":
                cntT += 1
                pointerT -= 1
                continue
                
            if cntS:
                cntS -= 1
                pointerS -= 1
                continue
                
            if cntT:
                cntT -= 1
                pointerT -= 1
                continue
                
            if i != j:
                return False
            
            pointerS -= 1
            pointerT -= 1
            
        return pointerS < 0 and pointerT < 0
```

### Results
**Time complexity**: *O*(n) for moving through every letters in two strings.

**Space complexity**: *O*(1) for storing *cntT, pointerT, cntS, pointerS*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200409%20%23844%20Backspace%20String%20Compare/1st%20trial.PNGG)
