# 200327 #160 Intersection of Two Linked Lists
Link: https://leetcode.com/problems/intersection-of-two-linked-lists/

## Description
Write a program to find the node at which the intersection of two singly linked lists begins.

For example, the following two linked lists:

    A: a1 - a2 - c1 - c2 - c3
    B: b1 - b2 - b3 - c1 - c2 - c3

begin to intersect at node c1.

**Example 1:**

    Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
    Output: Reference of the node with value = 8
    Input Explanation: The intersected node's value is 8 (note that this must not be 0 if the two lists intersect). From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,0,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.
 

**Example 2:**

    Input: intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
    Output: Reference of the node with value = 2
    Input Explanation: The intersected node's value is 2 (note that this must not be 0 if the two lists intersect). From the head of A, it reads as [0,9,1,2,4]. From the head of B, it reads as [3,2,4]. There are 3 nodes before the intersected node in A; There are 1 node before the intersected node in B.
 

**Example 3:**

    Input: intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
    Output: null
    Input Explanation: From the head of A, it reads as [2,6,4]. From the head of B, it reads as [1,5]. Since the two lists do not intersect, intersectVal must be 0, while skipA and skipB can be arbitrary values.
    Explanation: The two lists do not intersect, so return null.


**Notes:**

If the two linked lists have no intersection at all, return null.
The linked lists must retain their original structure after the function returns.
You may assume there are no cycles anywhere in the entire linked structure.
Your code should preferably run in O(n) time and use only O(1) memory.

## 1<sup>st</sup> trial

### Intuition
Let's assume that the linked list A and B, which begin to intersect at the node C1, exist as follows:

    A: a1 - a2 - ... - aN - c1 - c2 - ... cK (total N+K nodes)
    B: b1 - b2 - ... - bM - c1 - c2 - ... cK (total M+K nodes)
    
    (where N >= M)
 
If there is no intersection, we can say that c1 is Null.

Then, move the pointer of the linked list A to locate at N-M th node, and move the pointers of both linked lists one by one for M+K times.

While moving the pointers of both linked lists, check whether the two nodes pointed by the pointers are same and return if there exists an intersection. If not, the answer would be Null.


### Code
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        
        if not headA or not headB:
            return None
        
        i, j = headA, headB
        cntA, cntB = 0, 0
        
        while i.next:
            i = i.next
            cntA += 1
        
        while j.next:
            j = j.next
            cntB += 1
        
        i, j = headA, headB
        if cntA > cntB:
            for k in range(cntA - cntB):
                i = i.next
        else:
            for k in range(cntB - cntA):
                j = j.next
        
        for k in range(min(cntA, cntB)+1):
            if i == j:
                return i
            i, j = i.next, j.next
        return None
```

### Results
**Time complexity**: *O*(n) for moving through the linked list.

**Space complexity**: *O*(1) for storing *i, j, cntA, cntB*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200327%20%23160%20Intersection%20of%20Two%20Linked%20Lists/trial%201.PNG)
