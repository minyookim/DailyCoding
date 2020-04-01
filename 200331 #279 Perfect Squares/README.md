# 200331 #279 Perfect Squares
Link: https://leetcode.com/problems/perfect-squares/

## Description
Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n.

**Example 1:**

    Input: n = 12
    Output: 3 
    Explanation: 12 = 4 + 4 + 4.

**Example 2:**

    Input: n = 13
    Output: 2
    Explanation: 13 = 4 + 9.

## 1<sup>st</sup> trial

### Intuition
The first approach that came to my mind was dynamic programming, but I speculated that there might be some other mathematical regularities. After finding the least number of perfect square numbers, from 1 to 35, I observed that every integers can be expressed with at least 4 sum of perfect square numbers. I googled the internet and I found the regarding theorems as follows:

**Lagrange's four-square theorem**



**Legendre's three-square theorem**

    A natural number can be represented as the sum of three squares of integers {\displaystyle n=x^{2}+y^{2}+z^{2}}n=x^{2}+y^{2}+z^{2}
    if and only if n is not of the form {\displaystyle n=4^{a}(8b+7)}n = 4^a(8b + 7) for nonnegative integers a and b.
    https://en.wikipedia.org/wiki/Legendre%27s_three-square_theorem

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
