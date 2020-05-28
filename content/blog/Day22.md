+++
date = "2020-05-22T21:56:55+01:00"
title = "Sort Characters By Frequency: Day 22 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "stack"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Sort Characters By Frequency, the question for Day 22 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Sort Characters By Frequency: Problem Definition

Given a string, sort it in decreasing order based on the frequency of characters.

##### Examples:

    Input:
    "tree"

    Output:
    "eert"

    Explanation:
    'e' appears twice while 'r' and 't' both appear once.
    So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.

    Input:
    "cccaaa"

    Output:
    "cccaaa"

    Explanation:
    Both 'c' and 'a' appear three times, so "aaaccc" is also a valid answer.
    Note that "cacaca" is incorrect, as the same characters must be together.

    Input:
    "Aabb"

    Output:
    "bbAa"

    Explanation:
    "bbaA" is also a valid answer, but "Aabb" is incorrect.
    Note that 'A' and 'a' are treated as two different characters.

### Approach

Make a dictionary with the element and its count. Sort the dictionary based on count in descending order and reprint the dictinary in the new order.

### Solution

``` python    

    class Solution:
        def frequencySort(self, s: str) -> str:
            dic={}
            for i in s:
                if i in dic:
                    dic[i]=dic[i]+1
                else:
                    dic[i]=1
            
            dic=sorted(dic.items(), key=lambda x: x[1], reverse=True)
        
            k=""
            for i in range (0,len(dic)):
                k=k+(dic[i][0]*dic[i][1])
            return k

```


> while(!(succeed=try())); 


### Submission Stats
        
    35 / 35 test cases passed.
    Status: Accepted
    Runtime: 48 ms
    Memory Usage: 15.1 MB

>My runtime beats 62.73 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)