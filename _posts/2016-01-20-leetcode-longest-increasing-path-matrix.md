---
layout: post
title: Leetcode - Longest Increasing Path In A Matrix
---

### Analysis

In this [problem](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/), there is one key insight -- **There will be no cycles.** If we are a node `x,` and we have got there from some node `y,` we will never reach `x` again from `y` since the only valid moves from a node are to its neighbours that have a higher value than itself. Since we have travelled from `x` to `y,` by definition, `val(y) > val(x).` Since for every incremental step from `y,` we only go to values higher than `y,` we will never go back to `x.` 

### Algorithm

We define a dynamic programming state `dp[i][j]` as the longest path originating at point `(i, j).` We then recursively find this value for all `(i, j)` by using the property that we can potentially move in four directions if the value at the neighbour is greater than the current value. Note that if we have already found out the value for a particular `(i, j),` we just return this value from the cache.

### Code

<script src="https://gist.github.com/adijo/7dd9eb910a36e48eb153.js"></script>