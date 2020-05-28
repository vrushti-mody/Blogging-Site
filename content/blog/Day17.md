+++
date = "2020-05-17T21:56:55+01:00"
title = " Find All Anagrams in a String: Day 17 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python","String Matching"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Find All Anagrams in a String, the question for Day 17 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Find All Anagrams in a String: Problem Definition

Given a string **s** and a **non-empty** string **p**, find all the start indices of **p's** anagrams in **s**.

Strings consists of lowercase English letters only and the length of both strings **s** and **p** will not be larger than 20,100.

The order of output does not matter.

##### Examples:

    Input:
    s: "cbaebabacd" p: "abc"

    Output:
    [0, 6]

    Explanation:
    The substring with start index = 0 is "cba", which is an anagram of "abc".
    The substring with start index = 6 is "bac", which is an anagram of "abc".

    Input:
    s: "abab" p: "ab"

    Output:
    [0, 1, 2]

    Explanation:
    The substring with start index = 0 is "ab", which is an anagram of "ab".
    The substring with start index = 1 is "ba", which is an anagram of "ab".
    The substring with start index = 2 is "ab", which is an anagram of "ab".

### Approach

The approach is simple. The two strings should have the same count of alphabets if they are anagrams. We use one dictionary to store the lcount of letters in p. We then create another dictionary for s, which has the first len(p) letters. We check if the dictinaries are same. If yes, we add the index to the list. For each iteration, we decrement the count of the previous first element and increment the count for the new element.

### Solution

``` python    

    class Solution:
        def findAnagrams(self, s: str, p: str) -> List[int]:
            if len(s)<len(p):
                return []
            
            pdict={}
            sdict={}
            ans=[]
            for i in p:
                if i in pdict:
                    pdict[i]=pdict[i]+1
                else:
                    pdict[i]=1

            for i in range(0,len(p)):
                if s[i] in sdict:
                    sdict[s[i]]=sdict[s[i]]+1
                else:
                    sdict[s[i]]=1
            if sdict==pdict:
                ans.append(0)
            for i in range(1,len(s)-len(p)+1):
                sdict[s[i-1]]=sdict[s[i-1]]-1
                if sdict[s[i-1]]==0:
                    del sdict[s[i-1]]
                if s[len(p)+i-1] in sdict:
                    sdict[s[len(p)+i-1]]=sdict[s[len(p)+i-1]]+1
                else:
                    sdict[s[len(p)+i-1]]=1
                
                if sdict==pdict:
                    ans.append(i)
            return ans

```


> while(!(succeed=try())); 


### Submission Stats

    36 / 36 test cases passed.
    Status: Accepted
    Runtime: 144 ms
    Memory Usage: 14.9 MB


>My runtime beats 70.38 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)