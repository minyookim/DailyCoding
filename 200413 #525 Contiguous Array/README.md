# 200412 #1046 Last Stone Weight
Link: https://leetcode.com/problems/last-stone-weight/

## Description
We have a collection of stones, each stone has a positive integer weight.

Each turn, we choose the two heaviest stones and smash them together.  Suppose the stones have weights x and y with x <= y.  The result of this smash is:

If x == y, both stones are totally destroyed;
If x != y, the stone of weight x is totally destroyed, and the stone of weight y has new weight y-x.
At the end, there is at most 1 stone left.  Return the weight of this stone (or 0 if there are no stones left.)

**Example 1:**

    Input: [2,7,4,1,8,1]
    Output: 1
    
    Explanation: 
    We combine 7 and 8 to get 1 so the array converts to [2,4,1,1,1] then,
    we combine 2 and 4 to get 2 so the array converts to [2,1,1,1] then,
    we combine 2 and 1 to get 1 so the array converts to [1,1,1] then,
    we combine 1 and 1 to get 0 so the array converts to [1] then that's the value of last stone.
 

**Note:**

    1 <= stones.length <= 30
    1 <= stones[i] <= 1000


## 1<sup>st</sup> trial

### Intuition
First, sort the stone array. Then, pop two largest items and calculate the difference between the two. If the difference is a positive integer, insert the element into the sorted array. Repeat this until the length of the stones list becomes 0 or 1.

### Code
```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        import bisect 
        
        stones.sort()
        print(stones)
        
        while len(stones) > 1:
            tmp1 = stones.pop()
            tmp2 = stones.pop()
            newStone = tmp1 - tmp2
            
            if newStone:
                bisect.insort(stones, newStone) 
            print(stones)
        
        if len(stones) == 1:
            return stones[0]
        else:
            return 0
```

### Results
**Time complexity**: *O*(n<sup>2</sup>) such that each insertion process takes O(n) and the algorithm should repeat insertion process for n elements.

**Space complexity**: *O*(1) for storing *tmp1, tmp2, and newStone".

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200412%20%231046%20Last%20Stone%20Weight/1st%20trial.PNG)
