+++
date = "2020-05-14T21:56:55+01:00"
title = "  Implement Trie (Prefix Tree): Day 14 of May Leetcode Challenge"
tags = ["Competitive Coding","Algorithms","Data Structures","Python", "maths","trees"]
categories = ["Competitive Coding"]
draft = false
description = "My solution to  Implement Trie (Prefix Tree), the question for Day 14 of the May Leetcoding Challenge challenge"
weight = 10
+++

### Why Take The Challenge?

[Leetcode](https://leetcode.com/) is a platform to practice and improve your coding skills, targetting data structures, time and space complexity. It teaches you to translate problem statement into code. It is a great resource to prepare for technical interviews. It has a lot of interesting and helpful coding questions that can help you be better prepared for an interview. You can pass the technical interviews at elite tech companies like Facebook, Amazon, Apple, Netflix, and Google. LeetCode questions are often asked during interviews at these companies, some more than at others. 

> 'Think twice, code once'

### Pre-requisites
- Understanding of atleast one programming language
- Basic knowledge of data structures

###  Implement Trie (Prefix Tree): Problem Definition

Implement a trie with insert, search, and startsWith methods.

##### Examples:

    Trie trie = new Trie();

    trie.insert("apple");
    trie.search("apple");   // returns true
    trie.search("app");     // returns false
    trie.startsWith("app"); // returns true
    trie.insert("app");   
    trie.search("app");     // returns true 

### Note

- You may assume that all inputs are consist of lowercase letters `a-z`.
- All inputs are guaranteed to be non-empty strings.

### Approach

The approach is very straightforward. Save the words in a list on insertion. Check if the word is in the array on search and run a loop from start to length of the prefix to check for prefix.

### Solution

``` python    

    class Trie:

        def __init__(self):
            """
            Initialize your data structure here.
            """
            self.ans=[]

        def insert(self, word: str) -> None:
            """
            Inserts a word into the trie.
            """
            self.ans.append(word)
            

        def search(self, word: str) -> bool:
            """
            Returns if the word is in the trie.
            """
            if word in self.ans:
                return True
            return False
            

        def startsWith(self, prefix: str) -> bool:
            """
            Returns if there is any word in the trie that starts with the given prefix.
            
            """
            for ans1 in self.ans:
                if len(ans1)>=len(prefix):
                    flag=0
                    for i in range(0,len(prefix)):
                        if ans1[i]!=prefix[i]:
                            flag=1
                            break
                    if flag==0:
                        return True
            return False




# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
        

```


> while(!(succeed=try())); 


### Submission Stats

    15 / 15 test cases passed.
    Status: Accepted
    Runtime: 2960 ms
    Memory Usage: 20.2 MB


>I submitted the solution late, so I don't have my performance stats

If you are stuck at any point or have any doubts, drop a message [here](https://www.vrushtimody.me/)