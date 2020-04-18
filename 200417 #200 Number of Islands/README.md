# 200416 #678 Valid Parenthesis String
Link: https://leetcode.com/problems/valid-parenthesis-string/

## Description
Given a string containing only three types of characters: '(', ')' and '*', write a function to check whether this string is valid. We define the validity of a string by these rules:

    1. Any left parenthesis '(' must have a corresponding right parenthesis ')'.
    2. Any right parenthesis ')' must have a corresponding left parenthesis '('.
    3. Left parenthesis '(' must go before the corresponding right parenthesis ')'.
    4. '*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string.
    5. An empty string is also valid.

**Example 1:**

    Input: "()"
    Output: True
    
**Example 2:**

    Input: "(*)"
    Output: True

**Example 3:**

    Input: "(*))"
    Output: True

**Note:** The string size will be in the range [1, 100].


## 1<sup>st</sup> trial

### Intuition
If you traverse the list of strings from left, the number of "(" parenthesis should be always larger or same than the number of ")" and asterisks. Conversely, if you traverse the list from the right side, the number of ")" should be always larger or same than the number of the others. By single-passing the list, use two pointers that traverse from the left and right, respectively, count the numbers of "(", ")", and the asterisks, and see if two conditions that I described above are satisfied.

### Code
```python
class Solution:
    def checkValidString(self, s: str) -> bool:
        
        cnt1, cnt2, idx, buf1, buf2, lens = 0,0,0,0,0, len(s)
        while idx < lens:
            if s[idx] == "(":
                cnt1 += 1
            elif s[idx] == ")":
                cnt1 -= 1
            elif s[idx] == "*":
                buf1 += 1
                
            
            if s[-idx-1] == ")":
                cnt2 += 1
            elif s[-idx-1] == "(":
                cnt2 -= 1
            elif s[-idx-1] == "*":
                buf2 += 1
            
            if cnt1+buf1< 0 or cnt2+buf2< 0:
                return False
            
            idx += 1
        
        if cnt1 > buf1:
            return False
        return True
```

### Results
**Time complexity**: *O*(n) for single pass.

**Space complexity**: *O*(1) for storing *cnt1, cnt2, buf1, buf2, idx, and lens*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200416%20%23678%20Valid%20Parenthesis%20String/1st%20trial.PNG)
