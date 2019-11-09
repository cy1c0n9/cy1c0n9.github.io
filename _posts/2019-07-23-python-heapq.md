---
layout:     post
title:      "python heapq usage"
date:       2019-07-23 23:00:00 +0000
author:     "cy1c0n9"
header-img: "img/post-bg-2019.jpg"
tags:
    - python
---

## python heapq

heapq official guide and source code：[8.4.heapq-Heap queue algorithm](https://docs.python.org/2/library/heapq.html)

heapq only support min_heap, to use max_heap, try to flip the sign of the items

### implement heap sort

    #!/usr/bin/evn python
    #coding:utf-8

    from heapq import *

    def heapsort(iterable):
        h = []
        for value in iterable:
            heappush(h,value)
        return [heappop(h) for i in range(len(h))]

    if __name__=="__main__":
        print heapsort([1,3,5,9,2])

### heappush()

heapq.heappush(heap, item): push item into heap

### heappop()

heapq.heappop(heap): get the minimum item from heap and return

    >>> h = []
    >>> from heapq import *         # import heapq
    >>> h
    []
    >>> heappush(h,5)               # add values
    >>> heappush(h,2)
    >>> heappush(h,3)
    >>> heappush(h,9)
    >>> h                           # print h
    [2, 5, 3, 9]
    >>> heappop(h)                  # pop the minimum
    2
    >>> h
    [3, 5, 9]
    >>> h.append(1)                 # append value to the list
    >>> h                           # thus h is not a heap
    [3, 5, 9, 1]
    >>> heappop(h)                  # heappop will return the first item,
    3
    >>> heappush(h,2)               # now both 2 and 1 are sorted into a heap order
    >>> h
    [1, 2, 9, 5]
    >>> heappop(h)                  # pop 1
    1

### heapq.heappushpop(heap, item)

heappushpop is the union of heappush and heappop,

**note: it first apply heappush(heap,item), then, heappop(heap)**

    >>> h
    [1, 2, 9, 5]
    >>> heappop(h)
    1
    >>> heappushpop(h,4)            #heappush(h,4),heappop(h)
    2
    >>> h
    [4, 5, 9]

### heapq.heapify(x)

inline change a list into a heap, to ensure the correctness
x must be a list

    >>> a=[3,6,1]
    >>> heapify(a)
    >>> heappop(a)
    1
    >>> b=[4,2,5]                   # if b is not a heap
    >>> heappop(b)                  # it will pop the first item
    4
    >>> heapify(b)
    >>> heappop(b)
    2

### heapq.heapreplace(heap, item)

heappushpop is the union of heappush and heappop,

**note: it first apply heappop(heap), then, heappush(heap,item)**

    >>> a=[]
    >>> heapreplace(a,3)            # error if a is empty
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    IndexError: index out of range
    >>> heappush(a,3)
    >>> a
    [3]
    >>> heapreplace(a,2)            # first (heappop(a)->3),then（heappush(a,2))
    3
    >>> a
    [2]
    >>> heappush(a,5)  
    >>> heappush(a,9)
    >>> heappush(a,4)
    >>> a
    [2, 4, 9, 5]
    >>> heapreplace(a,6)            # pop the minimum and then push 6
    2
    >>> a
    [4, 5, 9, 6]
    >>> heapreplace(a,1)            # pop the minimum and then push 1
    4
    >>> a
    [1, 5, 9, 6]

###heapq.merge(\*iterables)

ex:

    >>> a=[2,4,6]         
    >>> b=[1,3,5]
    >>> c=merge(a,b)
    >>> list(c)
    [1, 2, 3, 4, 5, 6]


###heapq.nlargest(n, iterable[, key]),heapq.nsmallest(n, iterable[, key])

get largest n value or smallest n value:

    >>> a   
    [2, 4, 6]
    >>> nlargest(2,a)
    [6, 4]
