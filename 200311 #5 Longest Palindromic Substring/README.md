# 200310 #406 Queue Reconstruction by Height
Link: https://leetcode.com/problems/queue-reconstruction-by-height/

## Description
Suppose you have a random list of people standing in a queue. Each person is described by a pair of integers (h, k), where h is the height of the person and k is the number of people in front of this person who have a height greater than or equal to h. Write an algorithm to reconstruct the queue.

**Note:**
The number of people is less than 1,100.

**Example**

    Input:
    [[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]

    Output:
    [[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]

## 1<sup>st</sup> trial

### Intuition
To simplify the question, let's assume that there is no one of same height. Then, by definition, the tallest person, which means one having highest h, the k value of the person will be 0. The k value of the second tallest person should be 0 or 1. If the value is 0, the second tallest person should be at the front of the tallest person. Otherwise, the second tallest person should be at the back. If we extends further, we can solve this problem just by sorting the array by decreasing order and inserting the person at the k-th index.

If there is multiple persons with same height, we can simply treat them as the one with the larger k is taller than the one with the smaller k.

### Code
```python
class Solution:
    def reconstructQueue(self, people: List[List[int]]) -> List[List[int]]:
        
        ans = []
        
        from operator import itemgetter
        people.sort(key=itemgetter(1))
        people.sort(key=itemgetter(0), reverse=True)
        
        for i in people:
            ans.insert(i[1], i)
        
        return ans
```

### Results
**Time complexity**: *O*(n<sup>2</sup>) for inserting the n elements. You can check this website for the further information (https://wayhome25.github.io/python/2017/06/14/time-complexity/).

**Space complexity**: *O*(n) for storing *ans*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200310%20%23406%20Queue%20Reconstruction%20by%20Height/1st%20trial.PNG)

## Discussions
After solving the problem, I found this website (https://stackoverflow.com/questions/6666748/python-sort-list-of-lists-ascending-and-then-decending), stating that lambda expression can be used instead of itemgetter. This yields slightly better runtime and space performance.

![2nd trial](https://github.com/minyookim/DailyCoding/blob/master/200310%20%23406%20Queue%20Reconstruction%20by%20Height/2nd%20trial.PNG)
