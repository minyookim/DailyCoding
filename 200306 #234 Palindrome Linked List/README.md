# 200306 #264 Palindrome Linked List
Link: https://leetcode.com/problems/palindrome-linked-list/

## Description
Given a singly linked list, determine if it is a palindrome.

**Example 1:**

    Input: 1->2
    Output: false
    Example 2:

    Input: 1->2->2->1
    Output: true

**Follow up:**
Could you do it in O(n) time and O(1) space?

## 1<sup>st</sup> trial

### Intuition
First, find the middle point of the linked list using two pointers, one moving twice faster than the other one. Next, make a reverse linked list from the middle point. In the end, check whether the value of newly made reversed linked list match with the provided linked list.

### Code
```python
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        
        i, j, newHead = head, head, None
        
        while i and i.next:
            i, j = i.next.next, j.next
        
        while j:
            tmp, j.next, newHead = j.next, newHead, j
            j = tmp
        
        while newHead:
            if head.val != newHead.val:
                return False
            head, newHead = head.next, newHead.next
        
        return True
```

### Results
**Time complexity**: *O*(n) for finding the middle point, making another linked list, and checking the value during a single-pass.

**Space complexity**: *O*(1) for storing *i*, *j*, *tmp*. Note that it is not *O*(n), since it utilizes and modifies the premade linked list.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200306%20%23234%20Palindrome%20Linked%20List/1st%20trial.PNG)
