+++
date = "2020-05-03T21:56:55+01:00"
title = "Ransom Note: Day 3 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "String Matching"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Ransom Note, the question for Day 3 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Ransom Note: Problem Definition

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

##### Example 1:

    Input: ransomNote = "a", magazine = "b"
    Output: false

##### Example 2:

    Input: ransomNote = "aa", magazine = "ab"
    Output: false

##### Example 3:

    Input: ransomNote = "aa", magazine = "aab"
    Output: true

##### Constraints:

- You may assume that both strings contain only lowercase letters.

### Approach

The problem is similar to string matching. If occurance of the alphabets in the string should be magazine string should be greater than the ransom note string, the answer is true. Else it is false.

### Solution

``` python
    
    class Solution:
        def canConstruct(self, ransomNote: str, magazine: str) -> bool:
            
            mag = { "a": 0, "b": 0, "c": 0, "d": 0, "e": 0, "f": 0, "g": 0, "h": 0, "i": 0, "j": 0,"k": 0, "l": 0, "m": 0, "n": 0, "o": 0,"p": 0, "q": 0, "r": 0, "s": 0, "t": 0, "u": 0, "v": 0, "w": 0,"x": 0, "y": 0, "z": 0  
            }
            flag=0
            for i in magazine:
                mag[i]=mag[i]+1
            for i in ransomNote:
                mag[i]=mag[i]-1
                if(mag[i]<0):
                    flag=1
                    break
            if flag==0:
                return True
            else:
                return False
            

```


> while(!(succeed=try())); 


### Submission Stats

    127 / 127 test cases passed.
    Status: Accepted
    Runtime: 64 ms
    Memory Usage: 14 MB


>My runtime beats 50.03 % of the python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)