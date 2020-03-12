# 200312 #438 Find All Anagrams in a String
Link: https://leetcode.com/problems/find-all-anagrams-in-a-string/

## Description
Given a string s and a non-empty string p, find all the start indices of p's anagrams in s.

Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100.

The order of output does not matter.

**Example 1:**

    Input:
    s: "cbaebabacd" p: "abc"

    Output:
    [0, 6]

    Explanation:
    The substring with start index = 0 is "cba", which is an anagram of "abc".
    The substring with start index = 6 is "bac", which is an anagram of "abc".

**Example 2:**

    Input:
    s: "abab" p: "ab"

    Output:
    [0, 1, 2]

    Explanation:
    The substring with start index = 0 is "ab", which is an anagram of "ab".
    The substring with start index = 1 is "ba", which is an anagram of "ab".
    The substring with start index = 2 is "ab", which is an anagram of "ab".

## 1<sup>st</sup> trial

### Intuition
The brute-force algorithm that scans all the possible substrings with the length of p will solve the question. When checking whether the substring is an anagram of target string *p*, I used dictionary to count the frequency of each element in target string, which will yield O(k).

### Code
```python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        
        ans, dic = [], {}
        
        for i in p:
            if i in dic: dic[i] += 1
            else:        dic[i] = 1
        
        for i in range(len(s)-len(p)+1):
            tmp, subs, j = dic.copy(), s[i:i+len(p)], 0
            
            while j<len(p):
                if subs[j] not in tmp: j += len(p)
                elif tmp[subs[j]]<=0:  j += len(p)
                else:                  tmp[subs[j]] += -1
                j += 1
                
            if j == len(p):            ans.append(i)
        
        return ans
```

### Results
**Time complexity**: *O*(nk) for checking the n-k substrings. Each check will cost O(k). Here, n means length of *s* and k indicates length of *p*.

**Space complexity**: *O*(n) for storing *subs* and *tmp*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200312%20%23438%20Find%20All%20anagrams%20in%20a%20String/1st%20trial.PNG)

## 2<sup>nd</sup> trial

### Intuition
Although it worked well for short substrings, my first attempt ended in time limit excess. To improve runtime performance, I adjusted algorithms to update the changed values only (remove the first and add the last elements in *subs*). Furthermore, I found Counter function, which directly replaces the counting function I previously implemented.

### Code
```python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        
        from collections import Counter
        ans, pdic = [], Counter(p)
        
        if not len(s) or not len(p) or len(p)>len(s):
            return ans
        
        targetdic = Counter(s[0:len(p)])
        
        for i in range(len(s)-len(p)):
            if pdic == targetdic:
                ans.append(i)
            
            targetdic[s[i]] += -1
            targetdic[s[i+len(p)]] += 1
            targetdic += Counter() #Remove zero and negative values from Counter
            
        if pdic == targetdic:
            ans.append(i+1)
        
        return ans
```

### Results
**Time complexity**: *O*(nk) as same as above, but improved slightly by using Counter method.

**Space complexity**: *O*(n) for storing *subs* and *tmp*.

![2nd trial](https://github.com/minyookim/DailyCoding/blob/master/200312%20%23438%20Find%20All%20anagrams%20in%20a%20String/2nd%20trial.PNG)

## Discussions
If the algorithm checks only the updated elements, it would result in better runtime performance.
