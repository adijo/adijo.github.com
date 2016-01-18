---
layout: post
title: Leetcode - Palindrome Partitioning II
---

This [problem](https://leetcode.com/problems/palindrome-partitioning-ii/) was a two stage dynamic programming problem.

### Solution
For the input string, consider the suffixes in increasing order of length. If a particular suffix is a palindrome, our problem reduces to finding the minimum number of cuts required for the corresponding prefix plus one.

For example, for the string `ababaaa`,
Since `a` is a palindrome, we get `1 + f("ababaa")`
Since `aa` is a palindrome, we get `1 + f("ababa")`
Since `aaa` is a palindrome, we get `1 + f("abab")`

This goes on and we find the minimum of all these values.

Now all we need to do is to have a quick way in which to find out if a substring of `a` from `i` to `j` inclusive is a palindrome. This table can be built by the following recurrence.

`dp[i][j] = true if s[i] == s[j] and dp[i + 1][j - 1]`


### Code

<script src="https://gist.github.com/adijo/4cd7cce0873bd99c48e1.js"></script>