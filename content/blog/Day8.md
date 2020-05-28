+++
date = "2020-05-08T21:56:55+01:00"
title = "Check If It Is a Straight Line: Day 8 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "maths"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Check If It Is a Straight Line, the question for Day 8 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Check If It Is a Straight Line: Problem Definition

You are given an array `coordinates`, `coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.
##### Examples:

![Line](/img/line1.jpg "Line")

    Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
    Output: true

![Line](/img/line2.jpg "Line")

    Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
    Output: false

      
### Constraints:

- `2 <= coordinates.length <= 1000`
- `coordinates[i].length == 2`
- -`10^4 <= coordinates[i][0], coordinates[i][1] <= 10^4`
- `coordinates` contains no duplicate point.

### Hide Hint #1  
If there're only 2 points, return true.

### Hide Hint #2
Check if all other points lie on the line defined by the first 2 points.

### Hide Hint #3
Use cross product to check collinearity.

### Approach

We need to find if all points lie on the same line. Like the hint said, if there are 2 points we return true. If not, we use the first to lines to find the equation of the line and then put the other points in the equation to check if they satisfy the equation. If a point doesn't we return false, else we return true.

### Solution

``` python    

    class Solution:
        def checkStraightLine(self, coordinates: List[List[int]]) -> bool:
            x1=coordinates[0][0]
            y1=coordinates[0][1]
            x2=coordinates[1][0]
            y2=coordinates[1][1]
            if (x1-x2!=0):
                m=(y1-y2)/(x1-x2)
                for i in range(2,len(coordinates)):
                    x= coordinates[i][0]
                    y= coordinates[i][1]
                    if y-y1!=m*(x-x1):
                        return False
                return True
            else:
                for i in range(2,len(coordinates)):
                    x= coordinates[i][0]
                    
                    if x!= x1:
                        return False
                return True

```


> while(!(succeed=try())); 


### Submission Stats

    79 / 79 test cases passed.
    Status: Accepted
    Runtime: 56 ms
    Memory Usage: 14.1 MB


>My runtime beats  92.91 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)