+++
date = "2020-05-13T21:56:55+01:00"
title = " Remove K Digits: Day 13 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "maths"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Remove K Digits, the question for Day 13 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Remove K Digits: Problem Definition

Given a non-negative integer num represented as a string, remove k digits from the number so that the new number is the smallest possible.

**Note:**
- The length of num is less than 10002 and will be ≥ k.
- The given num does not contain any leading zero.

##### Examples:

    Input: num = "1432219", k = 3
    Output: "1219"
    Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.

    Input: num = "10200", k = 1
    Output: "200"
    Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.

    Input: num = "10", k = 2
    Output: "0"
    Explanation: Remove all the digits from the number and it is left with nothing which is 0.    

### Approach

The approach is check if the current number is greater than the preceeding number. If yes we remove the number. If no number is greater than the preceeding number, we remove the last number.

### Solution

``` python    

    class Solution:
        def removeKdigits(self, num: str, k: int) -> str:
            if len(num)==k:
                return "0"
            li=[]
            for i in range(0,len(num)):
                li.append(num[i])
                
            for j in range(0,k):
                i=0
                while i<len(li)-1 and int(li[i])<=int(li[i+1]):
                    i=i+1
                li.pop(i)
            s=""
            for i in li:
                s=s+i
            s=int(s)
            return str(s)
        

```


> while(!(succeed=try())); 


### Submission Stats

    33 / 33 test cases passed.
    Status: Accepted
    Runtime: 1324 ms
    Memory Usage: 13.9 MB


>I submitted the solution late, so I don't have my performance stats

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)