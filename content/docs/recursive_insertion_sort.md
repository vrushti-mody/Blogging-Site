+++
date = "2020-06-07T21:56:55+01:00"
title = "Recursion"
tags = ["algorithms","python","data structures","recursion","sort"]
categories = ["recursion"]
draft = false
description = "Section 3: Recursive Insertion Sort"
weight = 10
+++

### Recursive Insertion Sort

Do read the recursion blog before procedding with this sorting technique.

Base case: If list has length 1 or zero, return list
Inductive step:
- Inductively sort slice l[0:len(l)-1]
- Insert l[len(l)] into this sorted slice

##### Complexity

Let us assume that T(n) is the time to run insertion sort on length n
- Time T(n-1) to sort slice seq[0: n-1]
- n-1 steps to insert seq[n-1] to sorted slice

Recurrence
- T(n)= n-1 + T(n-1)
- T(1)= 1

Expanding, we get
T(n)= n-1 + T(n-1) = (n-1) + (n-2) + T(n-2) = .... = 
(n-1) + (n-2) + ..... + 1 = n(n-1)/2 = O(n2)

> Question to ponder: What happens when insertion sort is applied to an already sorted list?

##### Implementation in python

    def InsertionSort(seq):
        isSort(seq,len(seq)

    def isSort(seq,k): #Sort slice seq[0:k]
        if k>1:
            issort(seq,k-1)
            insert(seq,k-1)

    def insert(seq,k): #Insert seq[k] into sorted seq[0:k-1]
        pos=k
        while pos > 0 and seq[pos] < seq[pos-1]:
            (seq[pos],seq[pos-1])= (seq[pos-1],seq[pos])
            pos = pos - 1

