+++
date = "2020-05-12T21:56:55+01:00"
title = " Single Element in a Sorted Array: Day 12 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "maths"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Single Element in a Sorted Array, the question for Day 12 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Single Element in a Sorted Array: Problem Definition

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once. Find this single element that appears only once.

**Follow up**: Your solution should run in O(log n) time and O(1) space.

##### Examples:

    Input: nums = [1,1,2,3,3,4,4,8,8]
    Output: 2

    Input: nums = [3,3,7,7,10,11,11]
    Output: 10
      

### Constraints
- `1 <= nums.length <= 10^5`
- `0 <= nums[i] <= 10^5`

### Approach

The approach is to check if the number matches the next number from the front as well as back in one iteration reducing time to 0(n/4) since we check alternate numbers and check front as well as back.

### Solution

``` python    

    class Solution:
        def singleNonDuplicate(self, nums: List[int]) -> int:
            n=len(nums)
            if n==1:
                return nums[0]
            for i in range(0,n,2):
                if nums[i]!=nums[i+1]:
                    return nums[i]
                else:
                    if nums[n-1-i]!=nums[n-i-2]:
                        return nums[n-1-i]               

```


> while(!(succeed=try())); 


### Submission Stats

    14 / 14 test cases passed.
    Status: Accepted
    Runtime: 68 ms
    Memory Usage: 16.1 MB


>My runtime beats 88.84 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)