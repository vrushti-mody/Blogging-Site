+++
date = "2020-05-30T12:56:55+01:00"
title = "K Closest Points to Origin: Day 30 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "math"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to K Closest Points to Origin, the question for Day 30 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### K Closest Points to Origin: Problem Definition

We have a list of `points` on the plane.  Find the `K` closest points to the origin `(0, 0)`.

(Here, the distance between two points on a plane is the Euclidean distance.)

You may return the answer in any order.  The answer is guaranteed to be unique (except for the order that it is in.)`

##### Examples:

    Example 1:

    Input: points = [[1,3],[-2,2]], K = 1
    Output: [[-2,2]]
    Explanation: 
    The distance between (1, 3) and the origin is sqrt(10).
    The distance between (-2, 2) and the origin is sqrt(8).
    Since sqrt(8) < sqrt(10), (-2, 2) is closer to the origin.
    We only want the closest K = 1 points from the origin, so the answer is just [[-2,2]].

    Example 2:

    Input: points = [[3,3],[5,-1],[-2,4]], K = 2
    Output: [[3,3],[-2,4]]
    (The answer [[-2,4],[3,3]] would also be accepted.)

### Constraints:

1. `1 <= K <= points.length <= 10000`
2. `-10000 < points[i][0] < 10000`
3. `-10000 < points[i][1] < 10000`

### Approach
Sort the list based on sum of squares of elements of the list and return the first k elements.

### Solution 

``` python    

    class Solution:
        def kClosest(self, points: List[List[int]], K: int) -> List[List[int]]:
            points.sort(key = lambda K: K[0]**2 + K[1]**2) 
    
            return points[:K] 
            
```


> while(!(succeed=try())); 


### Submission Stats
            
    83 / 83 test cases passed.
    Status: Accepted
    Runtime: 668 ms
    Memory Usage: 19.1 MB

>My runtime beat 92.82 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)