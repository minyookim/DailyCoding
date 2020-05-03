# 200501 #278 First Bad Version
Link: https://leetcode.com/problems/first-bad-version/

## Description
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which will return whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

**Example:**

    Given n = 5, and version = 4 is the first bad version.

    call isBadVersion(3) -> false
    call isBadVersion(5) -> true
    call isBadVersion(4) -> true

    Then 4 is the first bad version. 


## 1<sup>st</sup> trial

### Intuition
Modifying binary search will find the answer.

### Code
```python
class Solution:
    def firstBadVersion(self, n):
        """
        :type n: int
        :rtype: int
        """
        
        start = 0
        end = n - 1
        
        while start <= end:
            mid = (start + end) // 2
            if isBadVersion(mid):
                end = mid - 1
            else:
                start = mid + 1
                
        return start
```

### Results
**Time complexity**: *O*(logn) for binary search.

**Space complexity**: *O*(1) for storing *start, mid, end*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200501%20%23278%20First%20Bad%20Version/1st%20trial.png)
