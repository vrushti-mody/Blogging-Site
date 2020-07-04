+++
date = "2020-06-05T21:56:55+01:00"
title = "Selection Sort"
tags = ["algorithms","python","data structures","sort"]
categories = ["sort"]
draft = false
description = "Section 2: Sorting in python, selection sort"
weight = 10
+++

### Selection sort:

- Select the next element in sorted order
- Move it into its correct place in the final sorted list

Pick the lowest number from the list and add it to another list.
Eg: Sort 74 32 89 55 21 64

Scan 1:
> Unsorted: 74 32 89 55 64
Sorted: 21

Scan 2:
> Unsorted: 74 89 55 64
Sorted: 21 32

Scan 3:
> Unsorted: 74 89 64
Sorted: 21 32 55

Scan 4:
> Unsorted: 74 89 
Sorted: 21 32 55 64

Scan 5:
> Unsorted: 89
Sorted: 21 32 55 64 74

Scan 6:
> Unsorted: 
Sorted: 21 32 55 64 74 89

We however do not need to maintain two lists for this. We can swap the minimum element with value in first position, aecond minimum with value in second place and so on

Scan 1: **21** 32 89 55 *74* 64 

Scan 2: 21 *32* 89 55 74 64

Scan 3: 21 32 **55** _89_ 74 64 

Scan 4: 21 32 55 **64** 74 _89_

##### Analysis of Selection Sort

- Finding minimum in unsorted segment of length **k** requires _k_ steps
- In each iteration, segment scan reduces by 1

- **T(n) = n+ (n-1) + (n-2)..... + 1 = n(n+1)/2 = O(n2)**

##### Implementation in python

    def SelectionSort(l):
        # Scan slices l[0:len(l)], l[1:len(l)]......
        for start in range(0,len(l)):
            #Find minimum value of slice
            minpos = start
            for i in range (start, len(l)):
                if l[i] < l[minpos]:
                    minpos = i
            (l[start],l[minpos])=(l[minpos],l[start])
        return l

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)