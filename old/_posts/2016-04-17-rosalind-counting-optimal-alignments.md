---
layout: post
title: Rosalind - Counting Optimal Alignments
tags:
- dynamic programming
- algorithms
---

### Analysis
*  In this [problem,](http://rosalind.info/problems/ctea/) we are asked to find the number of optimal edit alignments. I figured that at first, we can find the value of the actual optimal alignment. 
*  After doing this, we can define a recursive relation like so: For a string `s,` and string `t,` we define `dp[i][j]` to be the total number of alignments which have the optimal alignment value. Let this optimal alignment value (that we found in the previous step be `opt.`) 

*ARTICLE IN PROGRESS*

### Code

I felt like writing Java code in its full painful verbosity today,
so here you go.

<script src="https://gist.github.com/adijo/2e32e5d8f34d110ca2403ded4ccff3cd.js"></script>