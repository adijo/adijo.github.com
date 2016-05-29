---
layout: post
title: Rosalind - Fleury's Algorithm - Eulerian Path and Eulerian Cycle
---

This was an implementation [problem](http://rosalind.info/problems/ba3f/) and hence I will not be discussing the logic used. [This](https://www.youtube.com/watch?v=Lr6C8u-FDL8) is a very good explanation about this algorithm. It applies to both the algorithms - to find an eulerian path and eulerian circuit.

The only place where they differ are the choice of the starting node. 

*  Eulerian Cycle: The choice of start node does not matter.
*  Eulerian Path: The start node must be that node which has an outdegree that is one greater than its indegree.

### Code
<script src="https://gist.github.com/adijo/15347b2d708978380ee67d99558e52d4.js"></script>