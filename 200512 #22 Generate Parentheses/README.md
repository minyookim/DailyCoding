# 200512 #22 Generate Parentheses
Link: https://leetcode.com/problems/generate-parentheses/

## Description
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

        [
          "((()))",
          "(()())",
          "(())()",
          "()(())",
          "()()()"
        ]

## 1<sup>st</sup> trial

### Intuition


### Code
```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        
        def genEachStr(string, left, right):
            if len(string) == 2*n:
                ans.append(string)
                return
            if left < n:
                genEachStr(string+'(', left+1, right)
            if right < left:
                genEachStr(string+')', left, right+1)
        
        ans = []
        string, left, right = '', 0, 0
        
        genEachStr(string, left, right)
        return ans
```

### Results
**Time complexity**: *O*(a<sup>n</sup>).

**Space complexity**: *O*(n) for storing *ans*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200512%20%2322%20Generate%20Parentheses/1st%20trial.png)
