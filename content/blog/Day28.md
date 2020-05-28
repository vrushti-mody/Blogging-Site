+++
date = "2020-05-28T12:56:55+01:00"
title = " Counting Bits: Day 28 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "math"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to  Counting Bits, the question for Day 28 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Counting Bits: Problem Definition

Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

##### Examples:

    Input: 2
    Output: [0,1,1]

    Input: 5
    Output: [0,1,1,2,1,2]

##### Follow up:

It is very easy to come up with a solution with run time O(n*sizeof(integer)). But can you do it in linear time O(n) /possibly in a single pass?
Space complexity should be O(n).
Can you do it like a boss? Do it without using any builtin function like __builtin_popcount in c++ or in any other language.

##### Hint #1  
You should make use of what you have produced already.

##### Hint #2  
ivide the numbers in ranges like [2-3], [4-7], [8-15] and so on. And try to generate new range from previous.

##### Hint #3  
Or does the odd/even status of the number help you in calculating the number of 1s?

### Approach
Using the built in function bin to covert the number to binary and count the number of 1's in each number

### Solution 

``` python    

    class Solution:
        def countBits(self, num: int) -> List[int]:
            li=[]
            for i in range(0, num+1):
                a=bin(i)
                count=a.count('1') 
                li.append(count)
            return li
        

```


> while(!(succeed=try())); 


### Submission Stats
            
    15 / 15 test cases passed.
    Status: Accepted
    Runtime: 92 ms
    Memory Usage: 20.7 MB

>My runtime beat 52.23 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)