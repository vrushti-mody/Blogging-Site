+++
date = "2020-05-04T21:56:55+01:00"
title = " Number Complement: Day 4 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "Maths"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to  Number Complement, the question for Day 4 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Number Complement: Problem Definition

Given a *positive* integer `num`, output its complement number. The complement strategy is to flip the bits of its binary representation.

##### Example 1:

    Input: num = 5
    Output: 2
    Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.

##### Example 2:

    Input: num = 1
    Output: 0
    Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.


##### Constraints:

- The given integer num is guaranteed to fit within the range of a 32-bit signed integer.
- `num >= 1`
- You could assume no leading zero bit in the integer’s binary representation.
- This question is the same as [1009] (https://leetcode.com/problems/complement-of-base-10-integer/)

### Approach

This question expects you to know about the [2's complement](https://en.wikipedia.org/wiki/Two%27s_complement) of a binary number. For example, if the number is 6 (110), then the next number which is a power of 2 is 8 (1000). We want the difference of 7(111) and the given number(110). Thus, the answer is 8-6-1 = 1. 

### Solution

``` python
    
    class Solution:
        def findComplement(self, num: int) -> int:
            i=0
            number=1
            while(number<=num):
                i=i+1
                number=2**i
            return number-num-1    
                

```


> while(!(succeed=try())); 


### Submission Stats

    149 / 149 test cases passed.
    Status: Accepted
    Runtime: 32 ms
    Memory Usage: 13.9 MB


>runtime beats 56.07 % of python3 submissions.

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)