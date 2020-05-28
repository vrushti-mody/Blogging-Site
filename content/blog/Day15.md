+++
date = "2020-05-15T21:56:55+01:00"
title = " Maximum Sum Circular Subarray: Day 15 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Maximum Sum Circular Subarray, the question for Day 15 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Maximum Sum Circular Subarray: Problem Definition

Given a **circular array C** of integers represented by `A`, find the maximum possible sum of a non-empty subarray of `C`.

Here, a circular array means the end of the array connects to the beginning of the array.  (Formally, `C[i] = A[i]` when `0 <= i < A.length`, and `C[i+A.length] = C[i]` when `i >= 0`.)

Also, a subarray may only include each element of the fixed buffer A at most once.  (Formally, for a subarray `C[i], C[i+1], ..., C[j]`, there does not exist `i <= k1, k2 <= j` with `k1 % A.length = k2 % A.length`.)

##### Examples:

    Input: [1,-2,3,-2]
    Output: 3
    Explanation: Subarray [3] has maximum sum 3

    Input: [5,-3,5]
    Output: 10
    Explanation: Subarray [5,5] has maximum sum 5 + 5 = 10

    Input: [3,-1,2,-1]
    Output: 4
    Explanation: Subarray [2,-1,3] has maximum sum 2 + (-1) + 3 = 4
      
    Input: [3,-2,2,-3]
    Output: 3
    Explanation: Subarray [3] and [3,-2,2] both have maximum sum 3

    Input: [-2,-3,-1]
    Output: -1
    Explanation: Subarray [-1] has maximum sum -1

### Note
- `-30000 <= A[i] <= 30000`
- `1 <= A.length <= 30000`

### Hints

**Hint 1**
> For those of you who are familiar with the Kadane's algorithm, think in terms of that. For the newbies, Kadane's algorithm is used to finding the maximum sum subarray from a given array. This problem is a twist on that idea and it is advisable to read up on that algorithm first before starting this problem. Unless you already have a great algorithm brewing up in your mind in which case, go right ahead!

**Hint 2**
> What is an alternate way of representing a circular array so that it appears to be a straight array? Essentially, there are two cases of this problem that we need to take care of. Let's look at the figure below to understand those two cases:
![Case1](/img/circular1.png "Case1")



**Hint 3**
> The first case can be handled by the good old Kadane's algorithm. However, is there a smarter way of going about handling the second case as well?

### Approach

The approach to find the max sum using [Kadane algorithm](https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/) as suggested in the hints and compare it with the sum obtained considering corner cases. We chose the greater sum.
A video explaination for the Kadane algorithm can be found [here](https://www.youtube.com/watch?v=86CQq3pKSUw)

### Solution

``` python    

    class Solution:
        def maxSubarraySumCircular(self, a: List[int]) -> int:
            def kadane(a): 
                n = len(a) 
                max_so_far = -9999999999999
                max_ending_here = -9999999999999
                for i in range(0, n): 
                    max_ending_here = max_ending_here + a[i] 
                    if (max_ending_here < 0): 
                        max_ending_here = 0
                    if (max_so_far < max_ending_here): 
                        max_so_far = max_ending_here 
                return max_so_far 
            print(a)
            a1=[]
            for i in a:
                a1.append(i)
            n = len(a) 

            # Case 1: get the maximum sum using standard kadane's 
            # algorithm 
            max_kadane = kadane(a) 

            # Case 2: Now find the maximum sum that includes corner 
            # elements. 
            max_wrap = 0
            for i in range(0,n): 
                max_wrap += a[i] 
                a[i] = -a[i] 

            
            max_wrap = max_wrap + kadane(a) 
            print(a1)
            print(max(a1))
            if max(a1)<0:
                return max(a1)
            else:
    
                if max_wrap > max_kadane: 
                    return max_wrap 
                else: 
                    return max_kadane             

```


> while(!(succeed=try())); 


### Submission Stats

    109 / 109 test cases passed.
    Status: Accepted
    Runtime: 568 ms
    Memory Usage: 18.1 MB


>My runtime beats 74.94 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)