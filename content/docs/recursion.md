+++
date = "2020-06-08T21:56:55+01:00"
title = "Recursion"
tags = ["algorithms","python","data structures","recursion"]
categories = ["recursion"]
draft = false
description = "Section 3: Introduction to recursion"
weight = 10
+++


### Recursion-Inductive Definitions

Many Mathematic functions are naturally defined inductively

##### Factorial

- 0! = 1
- n! = n x (n-1)!

    def factiorial(n):
        if(n==0):
            return(1)
        else:
            return (n*factorial(n-1))

##### Multiplication

- m x 1 = m
- m x (n+1) = m + (m x n)

    def multiply (m,n):
        if(n==1):
            return(m)
        else:
            return (m + multiply (m,n-1))


##### Recursion works by 

- Define one or more base case
- Inductive step defines f(n) in terms of smaller arguements

### Inductive definition for Lists

Lists can be decomposed as 
- First (or last) element
- Remaining list with one less element

##### How to define list inductively?

- Base Case: Empty list or list of size 1
- Inductive step: f(l) in terms of smaller sublists of l

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)
