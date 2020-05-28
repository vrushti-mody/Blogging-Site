+++
date = "2020-05-16T21:56:55+01:00"
title = " Odd Even Linked List: Day 16 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "maths","linked-list"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Odd Even Linked List, the question for Day 16 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Odd Even Linked List: Problem Definition

Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.

You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.

##### Examples:

    Input: 1->2->3->4->5->NULL
    Output: 1->3->5->2->4->NULL

    Input: 2->1->3->5->6->4->7->NULL
    Output: 2->3->6->7->1->5->4->NULL

### Note
- `-30000 <= A[i] <= 30000`
- `1 <= A.length <= 30000`

### Constraints

- The relative order inside both the even and odd groups should remain as it was in the input.
- The first node is considered odd, the second node even and so on ...
- The length of the linked list is between [0, 10^4].





### Approach

The question may look difficult, but the approach is simple. Two pointers, one with start and one with start->next
the link to start will be start->next->next. i.e We iterate the even and odd by two and combine the lists after the linked list is interated completely

### Solution

``` python    

    # Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def oddEvenList(self, head: ListNode) -> ListNode:

        if head == None or head.next ==None:
            return head
        head1=head
        head2,head2_beg= head.next,head.next
        while head2.next!= None and head2.next.next!= None:
            head1.next = head2.next
            head2.next = head2.next.next
            head1 = head1.next
            head2 = head2.next
        if head2.next!=None:
            head1.next = head2.next
            head1 = head1.next
        head1.next = head2_beg
        head2.next = None
        return head            

```


> while(!(succeed=try())); 


### Submission Stats

    71 / 71 test cases passed.
    Status: Accepted
    Runtime: 40 ms
    Memory Usage: 15.9 MB


>My runtime beats 89.91 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)