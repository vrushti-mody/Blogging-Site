+++
date = "2020-05-19T21:56:55+01:00"
title = " Online Stock Span: Day 19 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "stack"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Online Stock Span, the question for Day 19 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Online Stock Span: Problem Definition

Write a class `StockSpanner` which collects daily price quotes for some stock, and returns the span of that stock's price for the current day.

The span of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backwards) for which the price of the stock was less than or equal to today's price.

For example, if the price of a stock over the next 7 days were `[100, 80, 60, 70, 60, 75, 85]`, then the stock spans would be `[1, 1, 1, 2, 1, 4, 6]`.
 
##### Examples:

    Input: ["StockSpanner","next","next","next","next","next","next","next"], [[],[100],[80],[60],[70],[60],[75],[85]]
    Output: [null,1,1,1,2,1,4,6]
    Explanation: 
    First, S = StockSpanner() is initialized.  Then:
    S.next(100) is called and returns 1,
    S.next(80) is called and returns 1,
    S.next(60) is called and returns 1,
    S.next(70) is called and returns 2,
    S.next(60) is called and returns 1,
    S.next(75) is called and returns 4,
    S.next(85) is called and returns 6.

    Note that (for example) S.next(75) returned 4, because the last 4 prices
    (including today's price of 75) were less than or equal to today's price.

### Note
- Calls to StockSpanner.next(int price) will have 1 <= price <= 10^5.
- There will be at most 10000 calls to StockSpanner.next per test case.
- There will be at most 150000 calls to StockSpanner.next across all test cases.
- The total time limit for this problem has been reduced by 75% for C++, and 50% for all other languages.
### Hints

**Hint 1**

Obviously, brute force will result in TLE. Think of something else.

**Hint 2**

How will you check whether one string is a permutation of another string?

**Hint 3**

One way is to sort the string and then compare. But, Is there a better way?

**Hint 4**

If one string is a permutation of another string then they must one common metric. What is that?

**Hint 5**

Both strings must have same character frequencies, if one is permutation of another. Which data structure should be used to store frequencies?

**Hint 6**

What about hash table? An array of size 26?



### Approach

We use a stack data structure for the question. We pop the topmost (in this case prior elements) till their value is less than or equal to current value and use a counter to increment the count. We return the count when we come across avalue greater than current value.

### Solution

``` python    

    class StockSpanner:

        def __init__(self):
            self.stack = [] 
            

        def next(self, price: int) -> int:
            current_span = 1
            while self.stack and self.stack[-1][0] <= price:
                p, span = self.stack.pop()
                current_span += span
            self.stack.append((price, current_span))
            return current_span

```


> while(!(succeed=try())); 


### Submission Stats
    
    99 / 99 test cases passed.
    Status: Accepted
    Runtime: 464 ms
    Memory Usage: 18.5 MB


>My runtime beats 91.94 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)