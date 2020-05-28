+++
date = "2020-05-06T21:56:55+01:00"
title = "Majority Element: Day 6 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "mode"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Majority Element, the question for Day 6 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Majority Element: Problem Definition

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊n/2⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

##### Examples:

    Input: [3,2,3]
    Output: 3


    Input: [2,2,1,1,1,2,2]
    Output: 2
      

### Approach

We need to find an element that appears more than n/2 times. For it to run at 0(n) we can iterate through the array and keep a dictionary with the elements and their counts. As soon as the count of an element crosses n/2 we should return the element. 

P.S: I just realised we can have two pointers, one at the start and one at the end for 0(n/2) time complexity. Try it out and let me know if it works.

### Solution

``` python    
    class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        di={}
        if len(nums)==1 or len(nums)==2:
            return nums[0]
        for i in nums:
            if i in di:
                di[i]=di[i]+1
                if di[i]>= len(nums)//2 +1:
                    return i
            else:
                di[i]=1

```


> while(!(succeed=try())); 


### Submission Stats

    46 / 46 test cases passed.
    Status: Accepted
    Runtime: 196 ms
    Memory Usage: 15.2 MB


>My runtime beats  14.60 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)