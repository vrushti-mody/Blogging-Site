+++
date = "2020-06-01T21:56:55+01:00"
title = "Introduction to Algorithms"
tags = ["algorithms","python","data structures"]
categories = ["algorithms"]
draft = false
description = "Getting Started with Algorithms (in Python)"
weight = 10
+++

### What is an Alogirthm?

- How to systematically perform a task
- Sequence of steps (Varying degrees of detail)

Algorithms can be used to/for:
- Compute numerical functions
- Reorganize data
- Optimization

### How to optimise an algorithm? An example

##### Computing the gcd of two numbers (m,n)

The most obvious solution is to find all factors of the two numbers, see which ones are common and return the greatest one:
``` python
    def gcd(m,n):
        fm=[]
        for i in range (1, m+1):
            if(m%i)==0:
                fm.append(i)
        fn=[]
        for j in range (1, n+1):
            if(n%j)==0:
                fn.append(j)
        cf=[]
        for f in fm:
            if f in fn:
                cf.append(f)
        return (cf[-1])
     
```

Optimization 1: Both the factors can be found in the same loop
``` python
    fm=[]
    fn=[]
    for i in range (1, max(m,n)+1): #assuming m>n
            if(m%i)==0:
                fm.append(i)
            elif (n%i==0):
                fn.append(i)
```

Optimization 2: We can reduce the loop to min (m,n) as the fcd cannot be greater than that. Also a common list can be used to save only the common divisors
``` python
    fm=[]
    fn=[]
    for i in range (1, min(m,n)+1): #assuming m>n
            if(m%i)==0 and (n%i==0):
                cf.append(i)
```

Optimization 3: The list can be replaced by a single number and since we want gcd, instead of searching from lowest to highest, we should search from highest to lowest. 
``` python
    i= min(m,n)
    while (m%i!=0 and n%i!=0):
        i=i-1
    return i
```

For further optimisation, you can read up on [Euclids Algorithm](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/the-euclidean-algorithm)


If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)

