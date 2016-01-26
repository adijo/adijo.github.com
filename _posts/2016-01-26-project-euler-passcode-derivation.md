---
layout: post
title: Project Euler - Passcode Derivation
---

This [problem](https://projecteuler.net/problem=79) required us to calculate the **longest path in a DAG.**

### Analysis

We build a graph out of the given dataset in the following way - If a certain passcode success was `321,` we create three nodes, `3, 2` and `1.` We add edges from `3` to `2` and from `2` to `1.` After building the graph, we find the longest path in this graph. This enables us to visit all the nodes and thus give us a valid passcode.

### Code
<script src="https://gist.github.com/adijo/34e3cc3ac5d8252ec2ee.js"></script>