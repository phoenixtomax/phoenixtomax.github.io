---
layout: default
title:  "LRU in Python"
author: Skipper
date:   2018-03-30 00:00:00 +0200
image: http://www.scrollpublishing.com/store/media/Thomas-Payne.jpg
---
# LRU in Python

```python
class LRUCache:
    def __init__(self, capacity):
        self.capacity = capacity
        self.tm = 0
        self.cache = {}
        self.lru = {}

    def get(self, key):
        if key in self.cache:
            self.lru[key] = self.tm
            self.tm += 1
            return self.cache[key]

        return -1

    def set(self, key, value):
        if len(self.cache) >= self.capacity:
            # find the LRU entry
            old_key = min(self.lru.keys(), key = lambda k:self.lru[k])
            self.cache.pop(old_key)
            self.lru.pop(old_key)
        self.cache[key] = value
        self.lru[key] = self.tm
        self.tm += 1
```

Here tm is the count for access (get success /set).
It guarantees that the latest entry isn't easily removed and the entry already added but seldem accessed is removed when set happens.

Profile:
> LRU cache took 1.440 sec

```python
import collections

class LRUCache:
    def __init__(self, capacity):
        self.capacity = capacity
        self.cache = collections.OrderedDict()

    def get(self, key):
        try:
            value = self.cache.pop(key)
            self.cache[key] = value
            return value
        except KeyError:
            return -1

    def set(self, key, value):
        try:
            self.cache.pop(key)
        except KeyError:
            if len(self.cache) >= self.capacity:
                self.cache.popitem(last=False)
        self.cache[key] = value
```
The least-used-item is in the head of OrderedDict, which is updated in get().

If there is no key when new key is during set(), firstly we check the capacity.
If capacity is reached, the head of OrderedDict is poped, then the head is empty for new key.

Profile:
> LRU cache took 0.096 sec

> Refs: https://www.kunxi.org/blog/2014/05/lru-cache-in-python/