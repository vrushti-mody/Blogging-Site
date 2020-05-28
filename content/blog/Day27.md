+++
date = "2020-05-27T21:56:55+01:00"
title = "Possible Bipartition: Day 27 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "graphs"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Possible Bipartition, the question for Day 27 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Possible Bipartition: Problem Definition

Given a set of `N` people (numbered 11, 2, ..., N1), we would like to split everyone into two groups of **any** size.

Each person may `dislike` some other people, and they should not go into the same group. 

Formally, if `dislikes[i] = [a, b]`, it means it is not allowed to put the people numbered `a` and `b` into the same group.

Return `true` if and only if it is possible to split everyone into two groups in this way.

##### Examples:

    Input: N = 4, dislikes = [[1,2],[1,3],[2,4]]
    Output: true
    Explanation: group1 [1,4], group2 [2,3]

    Input: N = 3, dislikes = [[1,2],[1,3],[2,3]]
    Output: false

    Input: N = 5, dislikes = [[1,2],[2,3],[3,4],[4,5],[1,5]]
    Output: false

##### Note:

- `1 <= N <= 2000`
- `0 <= dislikes.length <= 10000`
- `1 <= dislikes[i][j] <= N`
- `dislikes[i][0] < dislikes[i][1]`
- There does not exist `i != j` for which `dislikes[i] == dislikes[j]`.

### Approach
This is classical graph theory problem: you have graph, and you need to check if it can be bipartitioned: all nodes must be divided into two groups, such that there is not connections between nodes in each group. This can be easily done using dfs and if a loop is found we directly return false.

### Solution

``` python    

    class Solution:
        def dfs(self, start):
            if self.found_loop == 1: return        #early stop if we found odd cycle
        
            for neib in self.adj_list[start]:
                if self.dist[neib] > 0 and (self.dist[neib] - self.dist[start]) %2 == 0:
                    self.found_loop = 1
                elif self.dist[neib] < 0:  #not visited yet
                    self.dist[neib] = self.dist[start] + 1
                    self.dfs(neib)
        
        def possibleBipartition(self, N: int, dislikes: List[List[int]]) -> bool:
            self.adj_list = defaultdict(list)
            self.found_loop, self.dist = 0, [-1] *(N+1)
            
            for i,j in dislikes:
                self.adj_list[i].append(j)
                self.adj_list[j].append(i)
            
            for i in range(N):
                if self.found_loop: return False    #early stop if we found odd cycle
                
                if self.dist[i] == -1:    #not visited yet
                    self.dist[i] = 0
                    self.dfs(i)
            
            return True
        

```


> while(!(succeed=try())); 


### Submission Stats
            
    66 / 66 test cases passed.
    Status: Accepted
    Runtime: 772 ms
    Memory Usage: 19.3 MB

>My runtime beat 62.38 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)