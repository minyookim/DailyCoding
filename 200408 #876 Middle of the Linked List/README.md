# 200408 #876 Middle of the Linked List
Link: https://leetcode.com/problems/middle-of-the-linked-list/

## Description
Given a non-empty, singly linked list with head node head, return a middle node of linked list.

If there are two middle nodes, return the second middle node.

**Example 1:**

    Input: [1,2,3,4,5]
    Output: Node 3 from this list (Serialization: [3,4,5])
    The returned node has value 3.  (The judge's serialization of this node is [3,4,5]).
    Note that we returned a ListNode object ans, such that:
    ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.

**Example 2:**

    Input: [1,2,3,4,5,6]
    Output: Node 4 from this list (Serialization: [4,5,6])
    Since the list has two middle nodes with values 3 and 4, we return the second one.
 

**Note:**

    The number of nodes in the given list will be between 1 and 100.


## 1<sup>st</sup> trial

### Intuition
While going through the end of the linked list, add counter for every iterations.
Then, move the pointers by the counter divided by two. Return the pointer. 

### Code
```python
class Solution:
    def middleNode(self, head: ListNode) -> ListNode:
        
        cnt = 0
        pointer = head
        
        while pointer.next:
            pointer = pointer.next
            cnt += 1
        
        pointer = head
        for i in range(cnt//2):
            pointer = pointer.next
        
        if cnt%2:
            pointer = pointer.next
        
        return pointer
```

### Results
**Time complexity**: *O*(n) for two single passes.

**Space complexity**: *O*(1) for storing *cnt* and *pointer*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200408%20%23876%20Middle%20of%20the%20Linked%20List/1st%20trial.PNG)
