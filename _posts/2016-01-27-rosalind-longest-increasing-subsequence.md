---
layout: post
title: Rosalind - Longest Increasing Subsequence
---

This was a rather standard dynamic programming [problem](http://rosalind.info/problems/lgis/) of finding the longest increasing subsequence which is taught in most algorithm courses. One slight addition here is that it asks for both the longest increasing and longest decreasing subsequences. Although being a standard problem, one interesting thing that I did here **to prevent code duplication,** was to abstract the process of deciding the order of the elements. What this means is that -- The algorithm to find the longest increasing and longest decreasing subsequences is identical, the only place where they differ is in deciding if element `x` should be greater or lesser than `y.` This is abstracted out into a higher order function in my code. This could be avoided by simply running the same longest increasing subsequence algorithm on the reverse sequence and then returning the reversal of the result although this seemed more elegant. 

### Code
<script src="https://gist.github.com/adijo/74cc4750f98601b17856.js"></script>

