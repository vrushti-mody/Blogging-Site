+++
date = "2020-06-02T21:56:55+01:00"
title = "Linear Search"
tags = ["algorithms","python","data structures","search"]
categories = ["search"]
draft = false
description = "Section 1: Search in python, linear search"
weight = 10
+++

### Linear Search:

- Go through the list linearly
- Check if current element is equal to the target element
    - If yes, Stop
    - If no go to the next element and repear steps

Eg: Array 1 2 3 4 5 6 7 8 9 Find 4

> Scan 1: _1_,2,3,4,5,6,8,9 1!=4 

> Scan 1: 1,_2_,3,4,5,6,8,9 2!=4 

> Scan 1: 1,2,_3_,4,5,6,8,9 3!=4 

> Scan 1: 1,2,3,_4_,5,6,8,9 4=4, Stop 

##### Analysis of Linear Search

In the best possible case,

- The element being searched may be found at the first position.
- In this case, the search terminates in success with just one comparison.
- Thus in best case, linear search algorithm takes O(1) operations.

In the best possible case,

- The element being searched may be present at the last position or not present in the array at all.
- In the former case, the search terminates in success with n comparisons.
- In the later case, the search terminates in failure with n comparisons.
- Thus in worst case, linear search algorithm takes O(n) operations.
 
We have:

  **T(n) = O(n)**

##### Implementation in python

    def search(arr, n, x): 
        for i in range (0, n): 
            if (arr[i] == x): 
                return i; 
        return -1; 

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)

