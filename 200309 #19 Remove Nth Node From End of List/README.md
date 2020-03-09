# 200304 #19 Remove Nth Node From End of List
Link: https://leetcode.com/problems/remove-nth-node-from-end-of-list/

## Description
Given a linked list, remove the n-th node from the end of list and return its head.

**Example:**

    Given linked list: 1->2->3->4->5, and n = 2.
    After removing the second node from the end, the linked list becomes 1->2->3->5.

**Note:**

Given n will always be valid.

**Follow up:**

Could you do this in one pass?

## 1<sup>st</sup> trial

### Intuition
Here I will use two pointers, *target* and *tmp*. *Target* marks the (n-1)-th node before the *Tmp*. As *Tmp* moves along the linked list and reaches at the end of the linked list, *Target* will point the (n-1)-th node from the end of list. Remove the next node of the target will yield the answer.

### Code
```python
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        
        target = tmp = head
        
        for i in range(n):
            tmp = tmp.next
        
        if not tmp:
            return head.next
        
        while tmp and tmp.next:
            target = target.next
            tmp = tmp.next

        target.next = target.next.next
        
        return head
```

### Results
**Time complexity**: *O*(n) for a single-pass of the given linked list.

**Space complexity**: *O*(1) for storing *tmp* and *target*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200309%20%2319%20Remove%20Nth%20Node%20From%20End%20of%20List/1st%20trial.PNG)
