---
layout: post
title: Project Euler - Consecutive Prime Sum
---

This [problem](https://projecteuler.net/problem=50) required us to get one key insight. We carry out a brute force search across all possible sub arrays of varying lengths with one key speedup -- **not calculating sum of ranges every time.** Instead, we maintain a **prefix sum array** which is a cumulative sum array. As a concerete example, for the array `[1, 2, 3],` the prefix array is `[1, 3, 6].` We can now calculate the sum of any range in this array in constant time. The Python version of this code took way too long, so I did it in Java and it took about `28` seconds which is not so good, but still under the project euler guideline of 1 minute. I will be able to speed it up somewhat by doing things a little differently, but I am quite sleepy and unwell right now.


### Code

<script src="https://gist.github.com/adijo/8438fcd13a5514035dff.js"></script>