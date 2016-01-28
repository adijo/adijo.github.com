---
layout: post
title: Rosalind - Finding a Shared Spliced Motif
---

This was another standard [problem](http://rosalind.info/problems/lcsq/) from an algorithms course. One difference was to actually find the [longest common subsequence](https://en.wikipedia.org/wiki/Longest_common_subsequence_problem) and not just its length. I had not done this exercise before so it was informative to do so. It required an extra 10 lines of code that reconstructs the optimal subsequence by taking the dynamic programming table constructed as an input. I always prefer to write my dynamic programming code in a top down fashion because all the corner cases can be taken care of easily. Unfortunately that sometimes results in stack overflows and I had to increase the memory allocated to python to make this work which can be done quite easily using the `sys.setrecursionlimit()` call.

### Code

<script src="https://gist.github.com/adijo/961ff510323d4a03e1af.js"></script>