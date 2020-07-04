+++
date = "2020-06-06T21:56:55+01:00"
title = "Merge Sort"
tags = ["algorithms","python","data structures","sort"]
categories = ["sort"]
draft = false
description = "Section 2: Sorting in python, merge sort"
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

    def mergesort (A, left right):
        if right - left <= 1:
            return(A[left:right])
        if right - left > 1:
            mid = (left+right)//2
        L= mergesort(A, left, mid)
        R= mergesort(A,mid,right)
    return(merge(L,R))

    def merge(A,B):
        (C,m,n) = ([],len(A),len(B))
        (i,j) = (0,0)
        while i+j < m+n:
            if (i==m):
                C.append(B[j])
                j=j+1
            if (j==n):
                C.append(A[i])
                i=i+1
            elif A[i]<= B[j]:
                C.append(A[i])
                i=i+1
            elif A[i] > B[j]:
                C.append(B[j])
                j=j+1
        return (C)

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)