+++
date = "2020-05-02T21:56:55+01:00"
title = "Jewels and Stones: Day 2 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "String Matching"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Jewels and Stones, the question for Day 2 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Jewels and Stones: Problem Definition

You're given strings `J` representing the types of stones that are jewels, and `S` representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in `J` are guaranteed distinct, and all characters in `J` and `S` are letters. Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.

##### Example 1:

    Input: J = "aA", S = "aAAbbbb"
    Output: 3

##### Example 2:

    Input: J = "z", S = "ZZ"
    Output: 0
    Given n = 5, and version = 4 is the first bad version.

##### Note:

- S and J will consist of letters and have length at most 50.
- The characters in J are distinct.

### Approach

The problem is similar to string matching. We check if the element in the stone list is present in the jewel list. If yes, we increment the count by 1. 

### Solution

``` python
    
    class Solution:
    def numJewelsInStones(self, J: str, S: str) -> int:
        j=0
        i=0
        count=0
        while i<len(S):
            if j==len(J):
                j=0
                i=i+1
            elif S[i]==J[j]:
                i=i+1
                j=0
                count=count+1
            else:
                j=j+1
        return count
            

```


> while(!(succeed=try())); 


I completed the challenge late, so I dont have my performance stats.

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)