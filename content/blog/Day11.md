+++
date = "2020-05-11T21:56:55+01:00"
title = " Flood Fill: Day 11 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "maths","TCS"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Flood Fill, the question for Day 11 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Flood Fill: Problem Definition

An `image` is represented by a 2-D array of integers, each integer representing the pixel value of the image (from 0 to 65535).

Given a coordinate `(sr, sc)` representing the starting pixel (row and column) of the flood fill, and a pixel value `newColor`, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image.

##### Examples:

    Input: 
    image = [[1,1,1],[1,1,0],[1,0,1]]
    sr = 1, sc = 1, newColor = 2
    Output: [[2,2,2],[2,2,0],[2,0,1]]
    Explanation: 
    From the center of the image (with position (sr, sc) = (1, 1)), all pixels connected 
    by a path of the same color as the starting pixel are colored with the new color.
    Note the bottom corner is not colored 2, because it is not 4-directionally connected
    to the starting pixel.
      
### Note
- The length of `image` and `image[0]` will be in the range `[1, 50]`.
- The given starting pixel will satisfy `0 <= sr < image.length` and `0 <= sc < image[0].length`.
- The value of each color in `image[i][j]` and `newColor` will be an integer in `[0, 65535]`.

### Hint #1  
Write a recursive function that paints the pixel if it's the correct color, then recurses on neighboring pixels.


### Approach

The approach is a bfs type of approach where we iterate through the block from centre to the sides.

### Solution

``` python    

    class Solution:
        def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
            old_color = image[sr][sc]
            queue = [(sr, sc)]
            seen = set()
            tot_rows = len(image)
            tot_cols = len(image[0])
            while queue:
                nxt = []
                for x,y in queue:
                    image[x][y] = newColor
                    seen.add((x,y))
                    
                    if x and (x-1,y) not in seen and image[x-1][y] == old_color: 
                        nxt.append((x-1,y))
                    if y and (x,y-1) not in seen and image[x][y-1] == old_color:
                        nxt.append((x, y-1))
                    if x < tot_rows-1 and (x+1,y) not in seen and image[x+1][y] == old_color:
                        nxt.append((x+1, y))
                    if y < tot_cols-1 and (x,y+1) not in seen and image[x][y+1] == old_color:
                        nxt.append((x,y+1))
                
                queue = nxt
            
            return image                   

```


> while(!(succeed=try())); 


### Submission Stats

    277 / 277 test cases passed.
    Status: Accepted
    Runtime: 68 ms
    Memory Usage: 14 MB


>My runtime beats 98.78 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)