---
layout: post
title:  "Python Tips"
date:   2018-08-31 11:00:00 +0900
tags: [Programming, Python]
---

## Check if all elements in list are identicial

```python

values = [1, 1, 1, 1, 1, 1]
# set(values) -> {1}
len(set(values)) == 1

```

## Reduce

```python

>>> from functools import reduce
>>> f = lambda a,b: a if (a > b) else b
>>> reduce(f, [47,11,42,102,13])
102

```

## Lambda

```python

>>> sum = lambda x, y : x + y
>>> sum(3,4)
7
>>> 

```

## Map

```python

>>> a = [1, 2, 3, 4]
>>> b = [17, 12, 11, 10]
>>> list(map(lambda x, y : x+y, a, b))
[18, 14, 14, 14]

>>> list(map(lambda x : x * x, a))
[1, 4, 9, 16]

```

## Filter

{% highlight python %}

>>> fibonacci = [0,1,1,2,3,5,8,13,21,34,55]
>>> odd_numbers = list(filter(lambda x: x % 2, fibonacci))
[1, 1, 3, 5, 13, 21, 55]
>>> f = lambda x: x % 2
>>> odd_numbers = list(filter(f, fibonacci))
[1, 1, 3, 5, 13, 21, 55]

{% endhighlight %}

## lower upper case

```python

>>> a = 'abC'
>>> a.lower()
'abc'
>>> a.upper()
'ABC'

```

## combind two dictionaries

```python
>>> a = {'a':1, 'b':1}
>>> b = {'c':2, 'd':2}
>>> {**a, **b} # only for string key
{'a': 1, 'b': 1, 'c': 2, 'd': 2}

>>> dict(a, **b) # only for string key
{'a': 1, 'b': 1, 'c': 2, 'd': 2}

>>> dict(a.items() | b.items())
{'c': 2, 'b': 1, 'a': 1, 'd': 2}
```