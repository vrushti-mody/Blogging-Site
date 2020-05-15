+++
date = "2020-05-01T21:56:55+01:00"
title = "First Bad Version: Day 1 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "Binary Search", "Searching"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to First Bad Version, the question for Day 1 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### First Bad Version: Problem Definition

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have `n` versions `[1, 2, ..., n]` and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API `bool isBadVersion(version)` which will return whether `version` is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

##### Example:

Given n = 5, and version = 4 is the first bad version.

        call isBadVersion(3) -> false
        call isBadVersion(5) -> true
        call isBadVersion(4) -> true

### Approach

The problem is similar to finding an element in the list. Conventional methods like iterating through each element (linear search) will increase the time complexity. Therefore, a [binary search](https://www.geeksforgeeks.org/binary-search/) method should be applied to obtain the solution. 

### Configuring Cypress

``` python
    
    # The isBadVersion API is already defined for you.
    # @param version, an integer
    # @return an integer
    # def isBadVersion(version):

    class Solution:
        def firstBadVersion(self, n):
            """
            :type n: int
            :rtype: int
            """
            if n==1: 
                return 1
            begin=1
            end=n
            while begin<end:
                mid=begin+(end-begin)/2
                if isBadVersion(mid): 
                    end=mid
                else: 
                    begin=mid+1
            return begin


```


> while(!(succeed=try())); 


I completed the challenge late, so I dont have my performance stats.

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)