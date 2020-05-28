+++
date = "2020-05-25T21:56:55+01:00"
title = " Uncrossed Lines: Day 25 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "dynamic programming"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Uncrossed Lines, the question for Day 25 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Uncrossed Lines: Problem Definition

We write the integers of `A` and `B` (in the order they are given) on two separate horizontal lines.

Now, we may draw connecting lines: a straight line connecting two numbers `A[i]` and `B[j]` such that:

- `A[i] == B[j]`;
- The line we draw does not intersect any other connecting (non-horizontal) line.

Note that a connecting lines cannot intersect even at the endpoints: each number can only belong to one connecting line.

Return the maximum number of connecting lines we can draw in this way.

##### Examples:

![142](/img/142.png "142")

    Input: A = [1,4,2], B = [1,2,4]
    Output: 2
    Explanation: We can draw 2 uncrossed lines as in the diagram.
    We cannot draw 3 uncrossed lines, because the line from A[1]=4 to B[2]=4 will intersect the line from A[2]=2 to B[1]=2.

    Input: A = [2,5,1,2,5], B = [10,5,2,1,5,2]
    Output: 3

    Input: A = [1,3,7,1,7,5], B = [1,9,2,5,1]
    Output: 2

##### Note:

- `1 <= A.length <= 500`
- `1 <= B.length <= 500`
- `1 <= A[i], B[i] <= 2000`

##### Hint 1

Think dynamic programming. Given an oracle dp(i,j) that tells us how many lines A[i:], B[j:] [the sequence A[i], A[i+1], ... and B[j], B[j+1], ...] are uncrossed, can we write this as a recursion?

### Approach

We use an approach similar to Longest Common Subsequence to solve the problem. Read about it [`here`](https://www.tutorialspoint.com/design_and_analysis_of_algorithms/design_and_analysis_of_algorithms_longest_common_subsequence.htm)

### Solution

``` python    

    class Solution:
        def maxUncrossedLines(self, A: List[int], B: List[int]) -> int:
            dp = [[0]*len(A) for _ in range(len(B))]
            dp[0][0] = 1 if A[0] == B[0] else 0
            for index_i in range(1, len(dp)):
                dp[index_i][0] = dp[index_i-1][0]
                if A[0] == B[index_i]:
                    dp[index_i][0] = 1
            for index_j in range(1, len(dp[0])):
                dp[0][index_j] = dp[0][index_j-1]
                if B[0] == A[index_j]:
                    dp[0][index_j] = 1
            for index_i in range(1, len(dp)):
                for index_j in range(1, len(dp[0])):
                    if A[index_j] == B[index_i]:
                        dp[index_i][index_j] = max(dp[index_i-1][index_j-1] + 1, max(dp[index_i-1][index_j], dp[index_i][index_j-1]))
                    else:
                        dp[index_i][index_j] = max(dp[index_i-1][index_j-1], max(dp[index_i-1][index_j], dp[index_i][index_j-1]))
            return dp[len(B)-1][len(A)-1]

```


> while(!(succeed=try())); 


### Submission Stats
            
    74 / 74 test cases passed.
    Status: Accepted
    Runtime: 312 ms
    Memory Usage: 14.1 MB

>My runtime beats 31.97 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)