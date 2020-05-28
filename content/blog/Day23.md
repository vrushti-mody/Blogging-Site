+++
date = "2020-05-23T21:56:55+01:00"
title = " Interval List Intersections: Day 23 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "math"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to  Interval List Intersections, the question for Day 23 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Interval List Intersections: Problem Definition

Given two lists of **closed** intervals, each list of intervals is pairwise disjoint and in sorted order.

Return the intersection of these two interval lists.

*(Formally, a closed interval `[a, b]` (with `a <= b`) denotes the set of real numbers `x` with `a <= x <= b`.  The intersection of two closed intervals is a set of real numbers that is either empty, or can be represented as a closed interval.  For example, the intersection of [1, 3] and [2, 4] is [2, 3].)*

##### Examples:

![Interval](/img/interval1.png "Interval")

    Input: A = [[0,2],[5,10],[13,23],[24,25]], B = [[1,5],[8,12],[15,24],[25,26]]
    Output: [[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]

##### Note:

- `0 <= A.length < 1000`
- `0 <= B.length < 1000`
- `0 <= A[i].start, A[i].end, B[i].start, B[i].end < 10^9`

### Approach

If the start of the first list is less than or equal to the end of the second list and the end of the first list is greater than or equal to the start of the second list, they have an intersection. The intersection is the smaller of the ends and the greater of the starts. If there is no intersection, to determine which list to increment, we check the end of both lists. The list who's end number is smaller is incremented.

### Solution

``` python    

    class Solution:
        def intervalIntersection(self, A: List[List[int]], B: List[List[int]]) -> List[List[int]]:
            li=[]
            i=0
            j=0
            while(i<len(A) and j<len(B)):
                if(A[i][0]<=B[j][1] and A[i][1]>=B[j][0]):
                    li.append([max(A[i][0],B[j][0]),min(A[i][1],B[j][1])])
                if A[i][1]>=B[j][1]:
                    j=j+1
                else:
                    i=i+1
                
            return li

```


> while(!(succeed=try())); 


### Submission Stats
         
    86 / 86 test cases passed.
    Status: Accepted
    Runtime: 148 ms
    Memory Usage: 14.4 MB

>My runtime beats 97.25 % % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)