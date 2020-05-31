+++
date = "2020-05-29T12:56:55+01:00"
title = "Course Schedule: Day 29 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "search"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Course Schedule, the question for Day 29 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Course Schedule: Problem Definition

There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses-1`.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: `[0,1]`

Given the total number of courses and a list of prerequisite **pairs**, is it possible for you to finish all courses?

##### Examples:

    Input: numCourses = 2, prerequisites = [[1,0]]
    Output: true
    Explanation: There are a total of 2 courses to take. 
                To take course 1 you should have finished course 0. So it is possible.

    Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
    Output: false
    Explanation: There are a total of 2 courses to take. 
                To take course 1 you should have finished course 0, and to take course 0 you should
                also have finished course 1. So it is impossible.

### Constraints:

The input prerequisites is a graph represented by a list of edges, not adjacency matrices. Read more about how a graph is represented.
You may assume that there are no duplicate edges in the input prerequisites.
`1 <= numCourses <= 10^5`

##### Hint #1  
This problem is equivalent to finding if a cycle exists in a directed graph. If a cycle exists, no topological ordering exists and therefore it will be impossible to take all courses.

##### Hint #2  
Topological Sort via DFS - A great video tutorial (21 minutes) on Coursera explaining the basic concepts of Topological Sort.

##### Hint #3  
Topological sort could also be done via BFS.

### Approach
Making use of hint 2, I carried out topological sort via DFS.

### Solution 

``` python    

    class Solution:
        def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
            edge=defaultdict(list)
            for p in prerequisites:
                edge[p[0]].append(p[1]) # from:to 

            for k in range(numCourses): # for each start point
                stack=[k]
                visit=set()
                while stack:
                    node=stack.pop(0)
                    if visit and node==k:     # ignore the first start node
                        return False
                    if node not in visit:
                        visit.add(node)
                        stack+=edge[node]
            return True

```


> while(!(succeed=try())); 


### Submission Stats
            
    46 / 46 test cases passed.
    Status: Accepted
    Runtime: 572 ms
    Memory Usage: 15.2 MB

>My runtime beat 15.67 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)