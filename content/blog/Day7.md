+++
date = "2020-05-07T21:56:55+01:00"
title = "Cousins in Binary Tree: Day 7 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "trees"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Cousins in Binary Tree, the question for Day 7 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

### Cousins in Binary Tree: Problem Definition

In a binary tree, the root node is at depth `0`, and children of each depth `k` node are at depth `k+1`.

Two nodes of a binary tree are cousins if they have the same depth, but have **different parents**.

We are given the `root` of a binary tree with unique values, and the values `x` and `y` of two different nodes in the tree.

Return `true` if and only if the nodes corresponding to the values `x` and `y` are cousins.

 

##### Examples:

![Cousins1](/img/cousins1.png "Tree1")

    Input: root = [1,2,3,4], x = 4, y = 3
    Output: false

![Cousins2](/img/cousins2.png "Tree2")

    Input: root = [1,2,3,null,4,null,5], x = 5, y = 4
    Output: true

![Cousins3](/img/cousins3.png "Tree3")

    Input: root = [1,2,3,null,4], x = 2, y = 3
    Output: false
      
### Constraints:

The number of nodes in the tree will be between `2` and `100`.
Each node has a unique integer value from `1` to `100`.


### Approach

We need to find if two nodes are cousins. For this we need to carry out level order traversal of the tree. Once we find both the nodes, we need to check if they are in the same level. If yes, whether they have the same parent. This can be done using a queue with parent and level of node stored.

### Solution

``` python    
    #Definition for a binary tree node.
    class TreeNode:
        def __init__(self, val=0, left=None, right=None):
            self.val = val
            self.left = left
            self.right = right

    class Solution:
        def isCousins(self, root: TreeNode, x: int, y: int) -> bool:
            if root == None: 
                return False 

            parA = None 

            parB = None 

            q = []  

            tmp = TreeNode(-1)  

            q.append((root, tmp))  

            while len(q) > 0:   

                levSize = len(q)  
                while levSize:   

                    ele = q.pop(0)  
 
                    if ele[0].val == x:   
                        parA = ele[1]  

                    if ele[0].val == y:   
                        parB = ele[1]  
 
                    if ele[0].left:   
                        q.append((ele[0].left, ele[0]))  

                    if ele[0].right:   
                        q.append((ele[0].right, ele[0]))  
                    levSize -= 1

                    if parA and parB:  
                        break 

                if parA and parB:   
                    return parA != parB  

                if (parA and not parB) or (parB and not parA):  
                    return False 

            return False 
            

```


> while(!(succeed=try())); 


### Submission Stats

    104 / 104 test cases passed.
    Status: Accepted
    Runtime: 32 ms
    Memory Usage: 14 MB


>My runtime beats 64.19 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)