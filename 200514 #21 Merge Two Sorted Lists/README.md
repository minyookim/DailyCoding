# 200514 #21 Merge Two Sorted Lists
Link: https://leetcode.com/problems/merge-two-sorted-lists/

## Description
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

    Input: 1->2->4, 1->3->4
    Output: 1->1->2->3->4->4

## 1<sup>st</sup> trial

### Intuition
First, generate empty list node. While l1 and l2 are both present, if the value of l1 is smaller than the value of l2, append the value of l1 to the list node and move l1 one step. Otherwise, append the l2 to the linked list and move l2 one step. After either l1 or l2 reaches to the end, append the other linked list to the *ans* linked list.

### Code
```python
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        
        ans = tmp = ListNode(0)
        
        while l1 and l2:
            if l1.val <= l2.val:
                tmp.next, l1 = l1, l1.next
            else:
                tmp.next, l2 = l2, l2.next
            
            tmp = tmp.next
        
        if l1:
            tmp.next = l1
        else:
            tmp.next = l2
            
        return ans.next
```

### Results
**Time complexity**: *O*(n) for single pass of l1 and l2.

**Space complexity**: *O*(1) for storing *ans, tmp*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200514%20%2321%20Merge%20Two%20Sorted%20Lists/1st%20trial.png)
