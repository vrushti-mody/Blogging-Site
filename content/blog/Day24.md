+++
date = "2020-05-24T21:56:55+01:00"
title = " Construct Binary Search Tree from Preorder Traversal: Day 24 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "trees"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Construct Binary Search Tree from Preorder Traversal, the question for Day 24 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Construct Binary Search Tree from Preorder Traversal: Problem Definition

Return the root node of a **binary** search tree that matches the given `preorder` traversal.

*(Recall that a binary search tree is a binary tree where for every node, any descendant of `node.left` has a value `<` `node.val`, and any descendant of `node.right` has a value `>` `node.val`.  Also recall that a preorder traversal displays the value of the `node` first, then traverses `node.left`, then traverses `node.right`.)*

It's guaranteed that for the given test cases there is always possible to find a binary search tree with the given requirements.

##### Examples:



    Input: [8,5,1,7,10,12]
    Output: [8,5,10,1,7,null,12]

![Btree](/img/btree.png "Btree")

##### Note:

- `1 <= preorder.length <= 100`
- `1 <= preorder[i] <= 10^8`
- The values of `preorder` are distinct.

### Approach

The first element of preorder traversal is always root. We first construct the root. Then we find the index of first element which is greater than root. Let the index be ‘i’. The values between root and ‘i’ will be part of left subtree, and the values between ‘i+1’ and ‘n-1’ will be part of right subtree. Divide given pre[] at index “i” and recur for left and right sub-trees.

### Solution

``` python    

    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, val=0, left=None, right=None):
    #         self.val = val
    #         self.left = left
    #         self.right = right
    class Solution:
        def bstFromPreorder(self, preorder: List[int]) -> TreeNode:
            
    
            # The first element of pre[] is always root 
            root = TreeNode(preorder[0]) 
    
            s = [] 
    
            # append root 
            s.append(root) 
    
            i = 1
    
            # Iterate through rest of the size-1 
            # items of given preorder array 
            while ( i < len(preorder)):  
                temp = None
    
                # Keep on popping while the next value  
                # is greater than stack's top value.  
                while (len(s) > 0 and preorder[i] > s[-1].val):  
                    temp = s.pop() 
                
                # Make this greater value as the right child 
                # and append it to the stack 
                if (temp != None):  
                    temp.right = TreeNode(preorder[i]) 
                    s.append(temp.right) 
                
                # If the next value is less than the stack's top 
                # value, make this value as the left child of the  
                # stack's top node. append the new node to stack 
                else : 
                    temp = s[-1] 
                    temp.left = TreeNode(preorder[i]) 
                    s.append(temp.left) 
                i = i + 1
            
            return root 
      

```


> while(!(succeed=try())); 


### Submission Stats
         
    10 / 110 test cases passed.
    Status: Accepted
    Runtime: 36 ms
    Memory Usage: 14 MB

>My runtime beats 64.66 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)