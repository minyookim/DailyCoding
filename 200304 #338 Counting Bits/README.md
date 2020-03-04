# 200304 #338 Counting Bits
Link: https://leetcode.com/problems/counting-bits/

## Description
Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

Example 1:

    Input: 2
    Output: [0,1,1]
    Example 2:

    Input: 5
    Output: [0,1,1,2,1,2]
    Follow up:

It is very easy to come up with a solution with run time O(n*sizeof(integer)). But can you do it in linear time O(n) /possibly in a single pass?
Space complexity should be O(n).
Can you do it like a boss? Do it without using any builtin function like __builtin_popcount in c++ or in any other language.

## 1<sup>st</sup> trial

### Intuition
For this kind of questions (I call these sequence questions), I usually start with finding the regularity of the sequence by simply listing up the elements. Here, the sequence would be

    0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31
    0 1 1 2 1 2 2 3 1 2  2  3  2  3  3  4  1  2  2  3  2  3  3  4  2  3  3  4  3  4  4  5

To see the regularity at a glance, I will parse the sequence like this.

    0 | 1 | 2 3 | 4 5 6 7 | 8 9 10 11 12 13 14 15 | 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31
    0 | 1 | 1 2 | 1 2 2 3 | 1 2  2  3  2  3  3  4 |  1  2  2  3  2  3  3  4  2  3  3  4  3  4  4  5

For the i<sup>th</sup> phrase, the i-1<sup>th</sup> phrase is repeated once and (i-1<sup>th</sup> phrase + 1) follows. You can easily parse the sequence by using logarithm and power.

### Code
```python
class Solution:
    def countBits(self, num: int) -> List[int]:

        if num==0: return [0] #exception handling to prevent log2(0) occurs
        
        import math
        iterNum=math.ceil(math.log2(num))
        
        ans = [1] #initializing the ans list
        for i in range(iterNum):
            tmp=ans[pow(2,i)-1:pow(2,i+1)-1]
            ans=ans+tmp+[i+1 for i in tmp]

        return [0]+ans[0:num]
```

### Results
**Time complexity**: *O*(n) for incrementing the subarrays of *ans*. Note that time complexity is not *O(nlogn)*, since incrementing step occurs at most once for the elements in *ans*.

**Space complexity**: *O*(n) for storing *tmp* and *ans* array.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200304%20%23338%20Counting%20Bits/1st%20trial.PNG)

### Discussions
After I solved the problem as above, I realized that this may be easily solved by using dynamic programming, since *ans*[i] = *ans*[i//2]+i%2). This may result in better runtime and space performance.
