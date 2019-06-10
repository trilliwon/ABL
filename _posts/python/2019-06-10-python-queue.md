---
layout: post
title:  "Python stack & queue"
date:   2019-06-10 15:00:00 +0900
tags: [Programming, Python]
---


## [Queue](https://docs.python.org/3.7/library/queue.html#module-queue)

```python
import queue

que = queue.Queue()
que.put(1)
que.put(2)

que.get() # 1
que.get() # 2
```

## Stack

```python
stack = []
stack.append(1)
stack.append(2)
stack.pop() # 2
stack.pop() # 1
```
