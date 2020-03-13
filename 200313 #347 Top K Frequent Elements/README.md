# 200313 #347 Top K Frequent Elements
Link: https://leetcode.com/problems/top-k-frequent-elements/

## Description
Given a non-empty array of integers, return the k most frequent elements.

    Example 1:

    Input: nums = [1,1,1,2,2,3], k = 2
    Output: [1,2]
    
    
    Example 2:

    Input: nums = [1], k = 1
    Output: [1]

**Note:**

You may assume k is always valid, 1 ≤ k ≤ number of unique elements.

Your algorithm's time complexity must be better than O(n log n), where n is the array's size.

## 1<sup>st</sup> trial

### Intuition
From previous problems, I learned how to use Counter from collection library. Since this provides function that returns top k frequent elements, it will be super-easy to implement.

### Code
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        
        ans = []
        
        from collections import Counter
        tmp = Counter(nums)
        com = tmp.most_common(k)
        
        for (a,b) in com:
            ans.append(a)
        
        return ans
```

### Results
**Time complexity**: *O*(nlogk) for most_common function, which utilizes heapq function (https://stackoverflow.com/questions/29240807/python-collections-counter-most-common-complexity).

**Space complexity**: *O*(n) for storing *tmp*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200313%20%23347%20Top%20K%20Frequent%20Elements/1st%20trial.PNG)

## 2<sup>nd</sup> trial

### Intuition
Although it worked well, it will be better to solve this question without using specialized functions, especially from a learning standpoint. Here, I used dictionary which counts the frequency of each value and sort the dictionary with frequency by lambda function.

### Code
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        
        ans, dic = [], {}
        
        for i in nums:
            if i in dic: dic[i] += 1
            else : dic[i] = 1
        
        com = sorted(dic.items(), key = lambda item: item[1], reverse=True)
        
        for (a,b) in com:
            ans.append(a)
        
        return ans[:k]
```

### Results
**Time complexity**: *O*(nlogn) for sorting the dictionary.

**Space complexity**: *O*(n) for storing *nums* and *com*.

![2nd trial](https://github.com/minyookim/DailyCoding/blob/master/200313%20%23347%20Top%20K%20Frequent%20Elements/2nd%20trial.PNG)

## Discussions
It will be helpful for me to go deep into the heap function.
