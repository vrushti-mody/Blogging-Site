+++
date = "2020-05-18T21:56:55+01:00"
title = " Permutation in String: Day 18 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "String Matching"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to Permutation in String, the question for Day 18 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Permutation in String: Problem Definition

Given two strings **s1** and **s2**, write a function to return true if **s2** contains the permutation of **s1**. In other words, one of the first string's permutations is the **substring** of the second string.

 
##### Examples:

    Input: s1 = "ab" s2 = "eidbaooo"
    Output: True
    Explanation: s2 contains one permutation of s1 ("ba").

    Input:s1= "ab" s2 = "eidboaoo"
    Output: False

### Consraints
- The input strings only contain lower case letters.
- The length of both given strings is in range [1, 10,000].

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

The approach is similar to [Day 17 of the challenge](/blog/day17/). The two strings should have the same count of alphabets if they are anagrams. We use one dictionary to store the lcount of letters in p. We then create another dictionary for s, which has the first len(p) letters. We check if the dictinaries are same. If yes, we add the return True. For each iteration, we decrement the count of the previous first element and increment the count for the new element and do it until we find a match or we reach the end of the string.

### Solution

``` python    

    class Solution:
        def checkInclusion(self, s1: str, s2: str) -> bool:
            if len(s1)>len(s2):
                return False
            
            dict1={'a':0,'b':0,'c':0,'d':0,'e':0,'f':0,'g':0,'h':0,'i':0,'j':0,'k':0,'l':0,'m':0,'n':0,'o':0,'p':0,'q':0,'r':0,'s':0,'t':0,'u':0,'v':0,'w':0,'x':0,'y':0,'z':0}
            dict2={'a':0,'b':0,'c':0,'d':0,'e':0,'f':0,'g':0,'h':0,'i':0,'j':0,'k':0,'l':0,'m':0,'n':0,'o':0,'p':0,'q':0,'r':0,'s':0,'t':0,'u':0,'v':0,'w':0,'x':0,'y':0,'z':0}
            for i in range(0,len(s1)):
                dict1[s1[i]]=dict1[s1[i]]+1
                dict2[s2[i]]=dict2[s2[i]]+1
                
            if dict1==dict2:
                return True
            
            for j in range(1,len(s2)-len(s1)+1):
                dict2[s2[j-1]]=dict2[s2[j-1]]-1
                dict2[s2[j+len(s1)-1]]=dict2[s2[j+len(s1)-1]]+1
            
                if dict1==dict2:
                    return True
            return False

```


> while(!(succeed=try())); 


### Submission Stats

    103 / 103 test cases passed.
    Status: Accepted
    Runtime: 56 ms
    Memory Usage: 13.7 MB


>My runtime beats 94.81 % of python3 submissions

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)