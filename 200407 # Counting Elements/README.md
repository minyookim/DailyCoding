# 200407 # Counting Elements
Link: https://leetcode.com/problems/group-anagrams/

## Description
Given an integer array arr, count element x such that x + 1 is also in arr.

If there're duplicates in arr, count them seperately.

**Example 1:**

    Input: arr = [1,2,3]
    Output: 2
    Explanation: 1 and 2 are counted cause 2 and 3 are in arr.

**Example 2:**

    Input: arr = [1,1,3,3,5,5,7,7]
    Output: 0
    Explanation: No numbers are counted, cause there's no 2, 4, 6, or 8 in arr.


**Example 3:**

    Input: arr = [1,3,2,3,5,0]
    Output: 3
    Explanation: 0, 1 and 2 are counted cause 1, 2 and 3 are in arr.

**Example 4:**

    Input: arr = [1,1,2,2]
    Output: 2
    Explanation: Two 1s are counted cause 2 is in arr.
 

**Constraints:**

1 <= arr.length <= 1000
0 <= arr[i] <= 1000

## 1<sup>st</sup> trial

### Intuition
After making the Counter of each string, check whether it was previously generated. 
If so, append the string into the anagram array, and if not, append the string by making new array.

### Code
```python
class Solution:
    def countElements(self, arr: List[int]) -> int:
        
        arr.sort()
        ans, cnt = 0, 0
        
        for i in range(len(arr)-1):
            if arr[i+1]-arr[i] > 1:
                cnt =0
            if arr[i] == arr[i+1]:
                cnt += 1
            if arr[i]+1 == arr[i+1]:
                ans += (cnt + 1)
                cnt = 0
                
        return ans
```

### Results
**Time complexity**: *O*(nk) for searching through strcnt array.

**Space complexity**: *O*(n) for storing *strcnt and ans* array.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200406%20%2349%20Group%20Anagrams/1st%20trial.PNG)
