+++
date = "2020-05-05T21:56:55+01:00"
title = "First Unique Character in a String: Day 5 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "String Matching"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to First Unique Character in a String, the question for Day 5 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### First Unique Character in a String: Problem Definition

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

##### Examples:

    s = "leetcode"
    return 0.

    s = "loveleetcode",
    return 2.
      
##### Note
- You may assume the string contain only lowercase letters.

### Approach

This problem is similar to problem solved during [Day 3](https://blog.vrushtimody.me/blog/day3/). We first check the count of each element in the list and then return the index of the element with count equal to 1.

### Solution

``` python    
    class Solution:
        def firstUniqChar(self, s: str) -> int:
            order = {}
            counts = {}
            for x in range(0,len(s)): 
                if s[x] in counts:
                    
                    counts[s[x]] += 1
                else:
                    counts[s[x]] = 1 
                    order[s[x]]=x
            for x in order:
                if counts[x] == 1:
                    return order[x]
            return -1

```


> while(!(succeed=try())); 


### Submission Stats

    104 / 104 test cases passed.
    Status: Accepted
    Runtime: 120 ms
    Memory Usage: 13.9 MB


>My runtime beats 54.39 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)