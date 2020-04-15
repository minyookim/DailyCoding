# 200414 # Perform String Shifts
Link: https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/529/week-2/3299/

## Description
You are given a string s containing lowercase English letters, and a matrix shift, where shift[i] = [direction, amount]:

    direction can be 0 (for left shift) or 1 (for right shift). 
    amount is the amount by which string s is to be shifted.
    A left shift by 1 means remove the first character of s and append it to the end.
    Similarly, a right shift by 1 means remove the last character of s and add it to the beginning.

Return the final string after all operations.

**Example 1:**

    Input: s = "abc", shift = [[0,1],[1,2]]
    Output: "cab"
    Explanation: 
    [0,1] means shift to left by 1. "abc" -> "bca"
    [1,2] means shift to right by 2. "bca" -> "cab"

**Example 2:**

    Input: s = "abcdefg", shift = [[1,1],[1,1],[0,2],[1,3]]
    Output: "efgabcd"
    Explanation:  
    [1,1] means shift to right by 1. "abcdefg" -> "gabcdef"
    [1,1] means s**hift to right by 1. "gabcdef" -> "fgabcde"
    [0,2] means shift to left by 2. "fgabcde" -> "abcdefg"
    [1,3] means shift to right by 3. "abcdefg" -> "efgabcd"


**Constraints:**

1 <= s.length <= 100
s only contains lower case English letters.
1 <= shift.length <= 100
shift[i].length == 2
0 <= shift[i][0] <= 1
0 <= shift[i][1] <= 100


## 1<sup>st</sup> trial

### Intuition
Like a conveyor belt, elements in shift list move the string left or right. Since moving left cancels moving right, it will be better to add all the elements in shift first, to calculate the total amount of shifts. Then, modulo operation of the total count will yield the amount of shift.

### Code
```python
class Solution:
    def stringShift(self, s: str, shift: List[List[int]]) -> str:
        
        cnt = 0
        for [a,b] in shift:
            if a == 0:
                cnt += b
            if a == 1:
                cnt -= b
        
        cnt %= len(s)
        
        return s[cnt:len(s)] + s[0:cnt]
```

### Results
**Time complexity**: *O*(n) for single pass of shift list.

**Space complexity**: *O*(1) for storing *cnt, a, b*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200414%20%23%20Perform%20String%20Shifts/1st%20trial.PNG)
