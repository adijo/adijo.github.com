---
layout: post
title: Leetcode - Increasing Triplet Subsequence
use_math: true
---

This [problem](https://leetcode.com/problems/increasing-triplet-subsequence/) was quite tricky. I took some time and a hint to find this solution. I will first present the algorithm and then explain the intuition. 

*  Let $i$ be the smallest number found and $j$ be the second smallest. We initialize these to be positive infinity.
*  We iterate through the elements in the list one by one, updating $i$ to be the smallest number encountered so far, $j$ to be the second smallest.
*  If at any point we find that $i < j < k$, we return `True.`
*  At the end, if we don't find any such triplet, we return `False.`

### Code
<script src="https://gist.github.com/adijo/56193cd8a85c875622802163fb32ee95.js"></script>

### Intuition

*  Consider the the solution looks like the following with $i, j$ and $k$ having the same meaning as before. Our current algorithm obviously works. But how can we prove that if an answer exists, it always finds *an* answer.

`--(1)--i---(2)---j----(3)----k`

*  There are two cases for $i.$ Either $i$ is the smallest number in the region `1` and `2` or it is not. If it *is,* then our algorithm finds it. If it *is not,* then our algorithm finds the smallest element in regions `1` and `2,` call it $i^*$. This still satisfies the condition $ i^* < j < k.$

*  The same argument applies for $j.$ 

Thus, our algorithm finds a solution if one exists.
