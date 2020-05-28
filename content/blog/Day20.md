+++
date = "2020-05-20T21:56:55+01:00"
title = "  Kth Smallest Element in a BST: Day 20 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "trees"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to  Kth Smallest Element in a BST, the question for Day 20 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###   Kth Smallest Element in a BST: Problem Definition

Given a binary search tree, write a function `kthSmallest` to find the **k**th smallest element in it.
 
##### Examples:

    Input: root = [3,1,4,null,2], k = 1
     3
    / \
    1   4
    \
     2
    Output: 1

    Input: root = [5,3,6,2,4,null,null,1], k = 3
           5
          / \
         3   6
        / \
       2   4
      /
     1
    Output: 3


### Follow up:
What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? How would you optimize the kthSmallest routine?

### Constraints:

- The number of elements of the BST is between `1` to `10^4`.
- You may assume `k` is always valid, `1 ≤ k ≤ BST's total elements`.


### Hints

**Hint 1**

Try to utilize the property of a BST.

**Hint 2**

Try in-order traversal. 

**Hint 3**

What if you could modify the BST node's structure?

**Hint 4**

The optimal runtime complexity is O(height of BST).


### Approach

We use inorder traversal to go through the array in ascending order and find the k smallest element. (Hint 2)

### Solution

``` python    

    class Solution:
        def kthSmallest(self, root: TreeNode, k: int) -> int:
            count = 0
            ksmall = -9999999999 # store the Kth smallest  
            curr = root # to store the current node  

            while curr != None: 

                # Like Morris traversal if current does 
                # not have left child rather than  
                # printing as we did in inorder, we  
                # will just increment the count as the  
                # number will be in an increasing order  
                if curr.left == None: 
                    count += 1

                    # if count is equal to K then we  
                    # found the kth smallest, so store  
                    # it in ksmall  
                    if count == k:  
                        ksmall = curr.val  

                    # go to current's right child  
                    curr = curr.right 
                else: 

                    # we create links to Inorder Successor  
                    # and count using these links  
                    pre = curr.left  
                    while (pre.right != None and 
                        pre.right != curr):  
                        pre = pre.right  

                    # building links  
                    if pre.right == None: 

                        # link made to Inorder Successor  
                        pre.right = curr  
                        curr = curr.left 

                    # While breaking the links in so made  
                    # temporary threaded tree we will check  
                    # for the K smallest condition  
                    else: 

                        # Revert the changes made in if part  
                        # (break link from the Inorder Successor)  
                        pre.right = None

                        count += 1

                        # If count is equal to K then we  
                        # found the kth smallest and so  
                        # store it in ksmall  
                        if count == k: 
                            ksmall = curr.val  

                        curr = curr.right 
            return ksmall # return the found value


```


> while(!(succeed=try())); 


### Submission Stats
    
    91 / 91 test cases passed.
    Status: Accepted
    Runtime: 56 ms
    Memory Usage: 17.8 MB


>My runtime beats 66.12 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)