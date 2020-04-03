# 200402 #202 Happy Number
Link: https://leetcode.com/problems/happy-number/

## Description
Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

**Example: **

    Input: 19
    Output: true

    Explanation: 
    12 + 92 = 82
    82 + 22 = 68
    62 + 82 = 100
    12 + 02 + 02 = 1

## 1<sup>st</sup> trial

### Intuition
After several iterations, the given integer converges into 1 or loops endlessly in a cycle. I used memoization to track visited numbers. If the number equals the number that was previously visited, the loop stops. If the result is 1, return True or else, return False.

### Code
```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        ref = {'0':0,'1':1,'2':4,'3':9,'4':16,'5':25,'6':36,'7':49,'8':64,'9':81}
        visited = []
        
        while n not in visited:
            visited.append(n)
            n = sum([ref[i] for i in str(n)])
        
        if n == 1:
            return True
        else:
            return False
```

### Results
**Time complexity**: It is hard to define time complexity in this case depends on n...

**Space complexity**: *O*(n) if we define n as the numbers of visited integers.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200402%20%23202%20Happy%20Number/1st%20trial.PNG)
