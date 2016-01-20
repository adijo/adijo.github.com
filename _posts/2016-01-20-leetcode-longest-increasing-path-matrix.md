---
layout: post
title: Leetcode - Longest Increasing Path In A Matrix
---

### Analysis

In this [problem](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/), there is one key insight -- There will be no cycles. If you are a node `x`, and you have got there from some node `y`, you will never reach `x` again from `y` since the only valid moves from a node are to its neighbours that have a higher value than itself. Since you have arrived from `x` to `y`, by definition, `val(y) > val(x)`. Since for every incremental step from `y`, you only go to values higher than `y`, you will never go back to `x`. 

### Algorithm

We define a dynamic programming state `dp[i][j]` as the longest path originating at point `(i, j).` We then recursively find this value for all `(i, j)` by using the property that you can potentially move in four directions if the value at the neighbour is greater than the current value. Note that if you have already found out the value for a particular `(i, j)`, we just return this value from the cache.

### Code

<script src="https://gist.github.com/adijo/7dd9eb910a36e48eb153.js"></script>