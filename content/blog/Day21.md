+++
date = "2020-05-21T21:56:55+01:00"
title = "  Count Square Submatrices with All Ones: Day 21 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "dynamic programming"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Count Square Submatrices with All Ones, the question for Day 21 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###   Count Square Submatrices with All Ones: Problem Definition

Given a `m * n` matrix of ones and zeros, return how many **square** submatrices have all ones.
 
##### Examples:

    Input: matrix =
    [
    [0,1,1,1],
    [1,1,1,1],
    [0,1,1,1]
    ]
    Output: 15
    Explanation: 
    There are 10 squares of side 1.
    There are 4 squares of side 2.
    There is  1 square of side 3.
    Total number of squares = 10 + 4 + 1 = 15.

    Input: matrix = 
    [
    [1,0,1],
    [1,1,0],
    [1,1,0]
    ]
    Output: 7
    Explanation: 
    There are 6 squares of side 1.  
    There is 1 square of side 2. 
    Total number of squares = 6 + 1 = 7.


### Constraints:

- `1 <= arr.length <= 300`
- `1 <= arr[0].length <= 300`
- `0 <= arr[i][j] <= 1`


### Hints

**Hint 1**

Create an additive table that counts the sum of elements of submatrix with the superior corner at (0,0).

**Hint 2**

Loop over all subsquares in O(n^3) and check if the sum make the whole array to be ones, if it checks then add 1 to the answer. 

### Approach

We use dynamic programming to solve this question. The recurrence relation is to find the number of squares ending at a particular point, if the value of that point is 1.
The realtion is: `arr[i][j] = min( min(arr[i-1][j], arr[i][j-1]), arr[i-1][j-1]) + 1`

### Solution

``` python    

    class Solution:
        def countSquares(self, matrix: List[List[int]]) -> int:
         # Initialize count variable 
            N=len(matrix)
            M= len(matrix[0])
            a=matrix
            count = 0

            for i in range(1, N): 
                for j in range(1, M): 

                    # If a[i][j] is equal to 0 
                    if (a[i][j] == 0): 
                        continue

                    # Calculate number of 
                    # square submatrices 
                    # ending at (i, j) 
                    a[i][j] = min([a[i - 1][j],  
                            a[i][j - 1], a[i - 1][j - 1]])+1

            # Calculate the sum of the array 
            for i in range(N): 
                for j in range(M): 
                    count += a[i][j] 

            return count 


```


> while(!(succeed=try())); 


### Submission Stats
    
    32 / 32 test cases passed.
    Status: Accepted
    Runtime: 672 ms
    Memory Usage: 16.1 MB


>My runtime beats 77.14%  of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)