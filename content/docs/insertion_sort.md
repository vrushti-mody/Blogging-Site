+++
date = "2020-06-04T21:56:55+01:00"
title = "Insertion Sort"
tags = ["algorithms","python","data structures","sort"]
categories = ["sort"]
draft = false
description = "Section 2: Sorting in python, insertion sort"
weight = 10
+++

### Insertion sort:

- First Element: put in new stack
- Second element: 
    Lower than first? Below first (left of first)
    Higher? Above first (right of first)
- Third element;
    Insert in correct position w.r.t first and second element
Repeat this for each new element


Eg: Sort 74 32 89 55 21 64

Scan 1:
> Unsorted: 32 89 55 21 64
Sorted: 74

Scan 2:
> Unsorted: 89 55 21 64
Sorted: 32 74

Scan 3:
> Unsorted: 55 21 64
Sorted: 32 74 89

Scan 4:
> Unsorted: 21 64
Sorted: 32 55 74 89 

Scan 5:
> Unsorted: 89
Sorted:21 32 55 74 89 

Scan 6:
> Unsorted: 
Sorted: 21 32 55 64 74 89

We however do not need to maintain two lists for this. We start building the sorted sequence with one element. We pick the next element and insert it into its correct place in the already sorted sequence.

Eg: Sort 74 32 89 55 21 64

Scan 1: _**32** 74_ 89 55 21 64

Scan 2: _32 74 **89**_ 55 21 64

Scan 3:_32_ **55** _74 89_ 21 64 

Scan 4: **21** _32 55 74 89_ 64

Scan 5: _21 32 55_ **64** _74 89_

##### Analysis of Insertion Sort

- Insertion of a new value in sorted segment of length **k** requires upto _k_ steps in worst case
- In each iteration,sorted segment scan increases by 1

- **T(n) = 1 + 2 + ....n-1 = n(n-1)/2 = O(n2)**

##### Implementation in python

    def InsertionSort(seq):
    
        # Scan slices l[0:len(l)], l[1:len(l)]......

        for sliceEnd in range(0,len(seq)):
            #Find minimum value of slice
            pos = sliceEnd
            while pos>0 and seq[pos] < seq[pos-1]:
                (seq[pos],seq[pos-1])= (seq[pos-1],seq[pos])
                pos=pos-1
        return seq

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)