+++
date = "2020-06-03T21:56:55+01:00"
title = "Binary Search"
tags = ["algorithms","python","data structures","search"]
categories = ["search"]
draft = false
description = "Section 1: Search in python, binary search"
weight = 10
+++

### Binary Search:

Binary Search can only be applied to a sorted list. If the list is not sorted, add the time complexity of sorting to that of binary sort to determine the total complexity.

- Divide the list into two halves (left, center element, right)
- If element we are searching for is center element, stop
- If element is greater than center element, divide right half of list and repeat the steps
- If element is less than center element, divide left half of list and repeat the steps

Eg: Array 1 2 3 4 5 6 7 8 9 Find 1

Scan 1: Middle:1; 1<5
> Array: 1,2,3,4 

Scan 2: Middle:2; 1<2
> Array: 1

Scan 3: Middle:1; 1=1
> Stop

##### Analysis of Binary Search

Recurrence
T(n) = T(n/2) + c
T(n/2) = T(n/4)+c


- **T(n) = O(logn)**

##### Implementation in python

    #Note: Binary search only works when the list is sorted
    
    def bsearch (seq, v, l, r):
        if (r-l == 0):
            return(False) #element not present

        mid = (l+r)//2 #finding the middle element

        if(v == seq[mid]): #if sequence equal to the middle element return true
            return (True)

        if (v < seq[mid]):
            return (bsearch(seq,v,l,mid)) #search left half
        
        else:
            return (bsearch(seq,v,mid+1,r)) #search right half

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)