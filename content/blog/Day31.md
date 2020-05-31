+++
date = "2020-05-31T12:56:55+01:00"
title = "Edit Distance: Day 31 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "dynamic programming"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Edit Distance, the question for Day 31 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Edit Distance: Problem Definition

Given two words *word1* and *word2*, find the minimum number of operations required to convert word1 to word2.

You have the following 3 operations permitted on a word:

1. Insert a character
2. Delete a character
3. Replace a character

##### Examples:

    Input: word1 = "horse", word2 = "ros"
    Output: 3
    Explanation: 
    horse -> rorse (replace 'h' with 'r')
    rorse -> rose (remove 'r')
    rose -> ros (remove 'e')

    Input: word1 = "intention", word2 = "execution"
    Output: 5
    Explanation: 
    intention -> inention (remove 't')
    inention -> enention (replace 'i' with 'e')
    enention -> exention (replace 'n' with 'x')
    exention -> exection (replace 'n' with 'c')
    exection -> execution (insert 'u')


### Approach
For every element, we have 3 options: insert delete replace. We check which of these gives minimum nymber of operations in the final result and work accordingly.

### Solution 

``` python    

    class Solution:
        def minDistance(self, word1: str, word2: str) -> int:
            M, N = len(word1), len(word2)
            if M * N == 0:
                return M + N
            dp = [[0] * (N + 1) for i in range(M + 1)]

            for i in range(M + 1):
                dp[i][0] = i
            for i in range(N + 1):
                dp[0][i] = i
            for i in range(1, M + 1):
                for j in range(1, N + 1):
                    if word1[i - 1] == word2[j - 1]:
                        dp[i][j] = dp[i - 1][j - 1]
                    else:
                        dp[i][j] = 1 + min(dp[i - 1][j], min(dp[i][j - 1], dp[i - 1][j - 1]))
            return dp[M][N]
            
```


> while(!(succeed=try())); 


### Submission Stats
            
    1146 / 1146 test cases passed.
    Status: Accepted
    Runtime: 212 ms
    Memory Usage: 17.4 MB

>My runtime beat 36.36 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)