+++
date = "2020-05-26T21:56:55+01:00"
title = " Contiguous Array: Day 26 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "math"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Contiguous Array, the question for Day 26 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Contiguous Array: Problem Definition

Given a binary array, find the maximum length of a contiguous subarray with equal number of 0 and 1.

##### Examples:

    Input: [0,1]
    Output: 2
    Explanation: [0, 1] is the longest contiguous subarray with equal number of 0 and 1.

    Input: [0,1,0]
    Output: 2
    Explanation: [0, 1] (or [1, 0]) is a longest contiguous subarray with equal number of 0 and 1.

##### Note:

 The length of the given binary array will not exceed 50,000.

### Approach

Let's have a variable count initially equals 0 and traverse through nums. Every time we meet a 0, we decrease count by 1, and increase count by 1 when we meet 1. It's pretty easy to conclude that we have a contiguous subarray with equal number of 0 and 1 when count equals 0.

What if we have a sequence [0, 0, 0, 0, 1, 1]? the maximum length is 4, the count starting from 0, will equal -1, -2, -3, -4, -3, -2, and won't go back to 0 again. But wait, the longest subarray with equal number of 0 and 1 started and ended when count equals -2. We can plot the changes of count on a graph, as shown below. Point (0,0) indicates the initial value of count is 0, so we count the sequence starting from index 1. The longest subarray is from index 2 to 6. To find the maximum length, we need a dict to store the value of count (as the key) and its associated index (as the value). We only need to save a count value and its index at the first time, when the same count values appear again, we use the new index subtracting the old index to calculate the length of a subarray. A variable max_length is used to to keep track of the current maximum length.

### Solution

``` python    

    class Solution:
        def findMaxLength(self, nums: List[int]) -> int:
            count=0
            max_length=0
            table = {0: 0}
            for index, num in enumerate(nums, 1):
                if num == 0:
                    count -= 1
                else:
                    count += 1
                
                if count in table:
                    max_length = max(max_length, index - table[count])
                else:
                    table[count] = index
            
            return max_length

```


> while(!(succeed=try())); 


### Submission Stats
            
    555 / 555 test cases passed.
    Status: Accepted
    Runtime: 904 ms
    Memory Usage: 18.4 MB

>My runtime beat 72.38 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)