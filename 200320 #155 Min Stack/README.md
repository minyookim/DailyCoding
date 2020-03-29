# 200320 #155 Min Stack
Link: https://leetcode.com/problems/min-stack/

## Description
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

push(x) -- Push element x onto stack.

pop() -- Removes the element on top of the stack.

top() -- Get the top element.

getMin() -- Retrieve the minimum element in the stack.
 

**Example:**

    MinStack minStack = new MinStack();
    minStack.push(-2);
    minStack.push(0);
    minStack.push(-3);
    minStack.getMin();   --> Returns -3.
    minStack.pop();
    minStack.top();      --> Returns 0.
    minStack.getMin();   --> Returns -2.

## 1<sup>st</sup> trial

### Intuition
The only way to remove values in this min stack is using pop, which removes the element on top of the stack. This data structure has two properties:

    1. The order of the inputs is conserved
    2. Minimum value at specific timepoint keeps monotonically decreasing as the inputs get in.
        Input:          3 2 4 1 5 6 8 0
        Minimum value:  3 2 2 1 1 1 1 0

By utilizing these two properties, I implemented the min stack as below:

### Code
```python
class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.stack = []
        self.minArray = []

    def push(self, x: int) -> None:
        self.stack.append(x)
        if not self.minArray or x<=self.minArray[-1]:
            self.minArray.append(x)
    
    def pop(self) -> None:
        if not self.stack:
            return
        
        pop = self.stack.pop()
        
        if pop == self.minArray[-1]:
            self.minArray.pop()
        
        return pop          

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.minArray[-1]
```

### Results
**Time complexity**: *O*(1) for every operations.

**Space complexity**: *O*(n) for storing *stack* (and *minArray* in the worst case).

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200320%20%23155%20Min%20Stack/1st%20trial.PNG)
