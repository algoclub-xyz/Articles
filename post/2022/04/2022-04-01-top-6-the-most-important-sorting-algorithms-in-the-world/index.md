---
title: "Top 6 the most important sorting algorithms in the world"
date: "2022-04-01"
categories: 
  - "algorithms-and-data-structures"
tags: 
  - "algorithms"
  - "sorting"
---

Ho-ho-ho!

Today we are going to take a look at **THE MOST IMPORTANT SORTING ALGORITHMS IN THE WORLD!!!!1** You know, it is really hard to underestimate sorting algorithms. They are that much important as the sorting hat in Hogwarts!

![](images/sorting_hat.gif)

So, we will start from the famous BogoSort!

1\. Bogosort

The algorithm consists of two steps:

1. Shuffle the array
2. Check if this permutation is sorted

So, I always imagine that this algorithm like a clown who put all the permutations in the box. Shake the box and take one of them. If the array is not sorted he is making over emotional ugly face, haha.

![bassie en adriaan wtf GIF by Videoland](https://media0.giphy.com/media/elpqNjSDwi5waM3VJF/giphy.gif?cid=ecf05e47k0iq7e1ahxly2xiyj5pg0403fztgivz3q6qq54v3&rid=giphy.gif&ct=g)

Let's code and estimate the proposed idea.

```
import random

def bogosort(a):
    array = a
    
    while not is\_sorted(array):
        array = random.shuffle(a)
    return array

def is\_sorted(a):
    for i in range(0, len(a) - 1):
        if a\[i + 1\] <= a\[i\]:
            return False
    return True
```

This algorithm does not have an upper bound. In the worst case we can always shuffle the array without getting the right sorted permutation.

The middle case is much more interesting: we can approach the estimation from the probabilities theory. There are **_n!_** permutations of an array on size _**n**_. Among those permutations only one permutation is sorted, therefore the probability to take the sorted array is **_1/n!_**. On expectation, that means that to see the sorted array _**n!**_ of items will occur on average. Therefore, on average we will see **_n!_** permutations and we need additional **_n iterations_** to check if this permutation is sorted. The algorithm works for **_O(n \* n!)_** on average.

The lower bound is the simplest case. The first permutation is already sorted therefore we need only **_n iterations_** to check it. The lower bound is _**O(n)**_.

| **_Bound_** | **_Complexity_** |
| --- | --- |
| Upper | Does not have an upper bound |
| Middle | O(n \* n!) |
| Lower | O(n) |

2\. Bozosort

Bozosort is an "improved" version of the previous algorithm Bogosort. Was called after the famous clown as the algorithm is super simple and even child can understand it.

The algorithm:

1. We need to take a random pair in the array and shuffle it
2. Check if the resulted array is sorted otherwise return to the step one

Sounds simple! Let's implement the code:

```
import random

def bozosort(a):
    array = a
    
    while not is\_sorted(array):
        l = random.uniform(0, len(array))
        r = random.uniform(0, len(array))

        t = array\[l\]
        array\[r\] = array\[l\]
        array\[l\] = t

    return array

def is\_sorted(a):
    for i in range(0, len(a) - 1):
        if a\[i + 1\] <= a\[i\]:
            return False
    return True
```

The complexity estimations are pretty much similar to **_BogoSort_**.

| **_Bound_** | **_Complexity_** |
| --- | --- |
| Upper | Does not have an upper bound |
| Middle | O(n \* n!) |
| Lower | O(n) |

3\. Sleep Sort

Sleep sort is also a quite classic algorithm of sorting. The idea is pretty simple we need to go through the array elements. For every element we need to start a new thread and block them for the same amount of time as the element's value.

```
import \_thread
from time import sleep

def tick(i):
    sleep(i)
    print(i)

def sleep\_sort(a):
    for i in a:
        arg\_tuple = (i,)
        \_thread.start\_new\_thread(tick, arg\_tuple)
```

The algorithm works exact the same amount of time as the maximum element of the array.

| **_Bound_** | **_Complexity_** |
| --- | --- |
| Upper, Middle, and Lower | O(max(array)) |

4\. Gnome Sort

The algorithm has been called based on a concept of a Garden Gnome sorting his flowers pots. We can divide the algorithm into two steps:

1. A gnome is looking at 2 pots at the time. If the next pot is smaller than the previous one then they swap them and now are looking at the previous two pots (the previous pair)
2. If the next pot is bigger than the current one then they switch their attention to the next pair

The algorithm looks similar to the another famous algorithm Bubble Sort. Unfortunately, this algorithm is out of the current article's scope.

Before start implementing something we need to discuss the boundary cases: if there are no more pairs then they stop sort the pots; empty arrays are already sorted.

```
def gnomesort(a):
    index = 1

    while index < len(a):
        if index == 0:
            index += 1
        elif a\[index\] < a\[index - 1\]:
            (a\[index\], a\[index - 1\]) = (a\[index - 1\], a\[index\])
            index -= 1
        else:
            index += 1

    return a
```

| **_Bound_** | **_Complexity_** |
| --- | --- |
| Upper and Middle | O(n2) imagine the array sorted in reverse order. On average we will do **_(n \* (n - 1)) / 2_** operations. |
| Lower | O(n), if the array already sorted |

![](images/gnome.gif)

Sorted!!1!

5\. Stalin Sort

This is a pretty fast algorithm it requires only linear amount of iterations. We need to iterate through the array and evict all the elements that breaks the sorting order (smaller than the previous elements).

![](images/kill.gif)

```
def stalinsort(a):
    sorted = \[\]

    sorted.append(a\[0\])

    for i in range(1, len(a)):
        if a\[i\] >= sorted\[len(sorted) - 1\]:
            sorted.append(a\[i\])

    return sorted
```

| **_Bound_** | **_Complexity_** |
| --- | --- |
| Upper, Middle, and Lower | O(n) |

6\. God Sort

There are _**n!-1**_ arrays that contains exact the same elements as ours but in different order. The probability to create exact the same array as ours is **_1/n!_** (if the values are different). The idea of the algorithm is to accept that God have created this algorithm for a reason. No need to sort the array at all.

```
def godsort(a):
    return a
```

| **_Bound_** | **_Complexity_** |
| --- | --- |
| Upper, Middle, and Lower | O(1) |

That was top six the most important algorithms in the world.

Happy Fool April subs!
