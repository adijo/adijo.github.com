---
layout: post
title: Leetcode - Game of Life
---

This was an implementation [problem](https://leetcode.com/problems/game-of-life/) so there's not much to explain. One key point is that to transform the board *in place*, we use dummy variables called `MADE_ALIVE` and `MADE_DEAD` to indicate cells that are to be converted to `ALIVE` and `DEAD` respectively in the next iteration and are __not__ to be considered as `ALIVE` and `DEAD` for *this* iteration.

### Code
<script src="https://gist.github.com/adijo/108b9b861ceb16d20210daef6200a14b.js"></script>