# 200503 #383 Ransom Note
Link: https://leetcode.com/problems/ransom-note/

## Description
Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

**Note:**

    You may assume that both strings contain only lowercase letters.

    canConstruct("a", "b") -> false
    canConstruct("aa", "ab") -> false
    canConstruct("aa", "aab") -> true

## 1<sup>st</sup> trial

### Intuition
First, generate the Counter for the magazine. Then, while iterating through all the letters in ransomNote, check whether the letter is in the Counter and if so, reduce the number of Counter. If the letter is not in the Counter or the count in the Counter is less than 0, return False. 

### Code
```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        from collections import Counter
        
        dic = Counter(magazine)
        
        for i in ransomNote:
            if i in dic:
                if dic[i] <= 0:
                    return False
                else:
                    dic[i] -= 1
            else:
                return False
        
        return True
```

### Results
**Time complexity**: *O*(n) for single pass of the ransomNote and making the Counter for the magazine.

**Space complexity**: *O*(n) for storing dic.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200503%20%23383%20Ransom%20Note/1st%20trial.png)
