---
layout: post
title: Project Euler - Square Digit Chains
---

This [problem](https://projecteuler.net/problem=92) had a brute force solution, with an important speedup -- **memoization.**

### Solution

We define a boolean function `find` that returns true if the given input ends up at 89. Every time we find a result, we store it in a cache so that we need not recompute it. Our cache builds up but our program significantly speeds up.

<script src="https://gist.github.com/adijo/a920db47533d4fd2a6fe.js"></script>