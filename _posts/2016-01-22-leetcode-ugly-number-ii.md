---
layout: post
title: Leetcode - Ugly Numbers II
---

This [problem](https://leetcode.com/problems/ugly-number-ii/) seemed like it would be related to number theory but it was actually an application of two very important data structures -- a **priority queue** and a **set.**

### Analysis and Algorithm

We had to find the `nth` ugly number. Ugly numbers are those that have only `2, 3, 5` as prime factors. Hence, all the ugly numbers would be of the form `2^i 3^j 5^k` for some exponents `i, j, k.` 

To solve this problem, we simply enumerate all the ugly numbers till we reach the `nth` one. This can be done efficiently using the priority queue and a set. In the beginning, we start off the process by adding `2^0 3^0 5^0` to the priority queue with the priority equal to the number (in this case, `1`). The item associated with the priority is the *exponent signature,* which in this case is `(0, 0, 0).` 

In each iteration, we pop the element with the lowest priority. Let `(a, b, c)` be the *exponent signature* of the element. We then enumerate the next elements which have the following *exponent signature:* `(a + 1, b, c), (a, b + 1, c), (a, b, c + 1).` If these are **not** already added to the priority queue (this is where the **set** comes into the picture), then we add them with priority `2^a 3^b 5^c.` When we pop the `nth` number, we know that this is the `nth` ugly number and we return it.

### Code
<script src="https://gist.github.com/adijo/4bdaf614dc4c3acfb7f0.js"></script>