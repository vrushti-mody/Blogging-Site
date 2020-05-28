+++
date = "2020-05-09T21:56:55+01:00"
title = " Valid Perfect Square: Day 9 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "maths"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to  Valid Perfect Square, the question for Day 9 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Valid Perfect Square: Problem Definition

Given a **positive** integer num, write a function which returns True if num is a perfect square else False.

**Follow up: Do not** use any built-in library function such as `sqrt`.

##### Examples:

    Input: num = 16
    Output: true

    Input: num = 14
    Output: false
      
### Constraints:

- `1 <= num <= 2^31 - 1`


### Approach

We cannot use inbuilt square root functions. However if we raise the number to 0.5, we get the square root. We then check if the square root has decimals. If not, its a perfect square.

### Solution

``` python    

    class Solution:
        def isPerfectSquare(self, num: int) -> bool:
            num=num**0.5
            print( num)
            num=str(num)
            if num[len(num)-1]=='0':
                return True
            else:
                return False

```


> while(!(succeed=try())); 


### Submission Stats

    70 / 70 test cases passed.
    Status: Accepted
    Runtime: 24 ms
    Memory Usage: 13.9 MB


>My runtime beats  93.55 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)