# 200318 #56 Merge Intervals
Link: https://leetcode.com/problems/merge-intervals/

## Description
Given a collection of intervals, merge all overlapping intervals.

**Example 1:**

    Input: [[1,3],[2,6],[8,10],[15,18]]
    Output: [[1,6],[8,10],[15,18]]
    Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].

**Example 2:**

    Input: [[1,4],[4,5]]
    Output: [[1,5]]
    Explanation: Intervals [1,4] and [4,5] are considered overlapping.

**NOTE**: input types have been changed on April 15, 2019. Please reset to default code definition to get new method signature.

## 1<sup>st</sup> trial

### Intuition
Here I implemented rule-based algorithm. First, sort the list by the first element. Then, you have to do is comparing whether the second element of the former is smaller than the first element of the latter. If so, append the former and move to the next interval. If not, merge the two intervals. While merging, compare whether the second element of the latter is larger than that of the former and if so, change the second element of the former into that of the latter.

### Code
```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        
        intervals.sort()
        
        if not intervals: return intervals
        ans = [intervals[0]]
        
        for i in range(1, len(intervals)):
            if ans[-1][1] < intervals[i][0]:
                ans.append(intervals[i])
            else:
                if ans[-1][1] < intervals[i][1]:
                    ans[-1][1] = intervals[i][1]
        
        return ans
```

### Results
**Time complexity**: *O*(n<sup>logn</sup>) for sorting the intervals.

**Space complexity**: *O*(n) for storing *ans*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200318%20%2356%20Merge%20Intervals/1st%20trial.PNG)
