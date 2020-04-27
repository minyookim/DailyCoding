# 200424 #146 LRU Cache
Link: https://leetcode.com/problems/lru-cache/

## Description
Design and implement a data structure for Least Recently Used (LRU) cache. It should support the following operations: get and put.

    get(key) - Get the value (will always be positive) of the key if the key exists in the cache, otherwise return -1.
    put(key, value) - Set or insert the value if the key is not already present. When the cache reached its capacity, it should invalidate the least recently used item before inserting a new item.

The cache is initialized with a positive capacity.

**Follow up:**
Could you do both operations in O(1) time complexity?

**Example:**

    LRUCache cache = new LRUCache( 2 /* capacity */ );

    cache.put(1, 1);
    cache.put(2, 2);
    cache.get(1);       // returns 1
    cache.put(3, 3);    // evicts key 2
    cache.get(2);       // returns -1 (not found)
    cache.put(4, 4);    // evicts key 1
    cache.get(1);       // returns -1 (not found)
    cache.get(3);       // returns 3
    cache.get(4);       // returns 4
 

## 1<sup>st</sup> trial

### Intuition


### Code
```python
class LRUCache:
    from collections import OrderedDict

    def __init__(self, capacity: int):
        self.capa = capacity
        self.dict = OrderedDict()

    def get(self, key: int) -> int:
        if key not in self.dict:
            return -1
        self.dict.move_to_end(key)
        return self.dict[key]

    def put(self, key: int, value: int) -> None:
        if key not in self.dict:
            if len(self.dict) >= self.capa:
                self.dict.popitem(last=False)
            self.dict[key] = value
        else:
            self.dict.move_to_end(key)
            self.dict[key] = value
```

### Results
**Time complexity**: *O*(1) for getting the key and putting the value into the dictionary.

**Space complexity**: *O*(n) for storing *self.dict*.

![1st trial](https://github.com/minyookim/DailyCoding/blob/master/200424%20%23146%20LRU%20Cache/1st%20trial.png)
