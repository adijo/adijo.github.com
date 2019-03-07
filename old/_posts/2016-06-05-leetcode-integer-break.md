---
layout: post
title: Leetcode - Integer Break
---

This [problem](https://leetcode.com/problems/integer-break/) was a modification of the popular dynamic programming problem based on rod cutting with some twists. 

### Analysis
*  For an integer `i`, we define a dynamic programming state `dp[i]` which indicates the maximum product you can get for integers that sum up to `i.` (the quantity required by the problem).

*  For a fixed `i,` we consider all possibilities for `j` from `[1 ... i - 1]`
   and find a maximum value amongst all those tuples. Thus, to find `dp[i],` we have `j` going from `[1 ... i - 1]` and we find the maximum value for `max(dp[j], j) * max(dp[i - j], i - j).` The reason we take the `max` operation here can be explained best with an example.
*  Consider finding `dp[8].` We iterate to get tuples `(7, 1), (6, 2), (5, 	  3), (4, 4).` Now, the maximum is obtained with `(6, 2).` If we just used `dp[6] * dp[2],` we would not get the correct answer as the `dp` part does not include the number itself. My explanation of this is not a very good one but I am quite sleepy right now ;). Just work out the `dp[8]` example by hand and you will figure it out.

### Code
<script src="https://gist.github.com/adijo/6676547766e649833f3d4636e97a0595.js"></script>