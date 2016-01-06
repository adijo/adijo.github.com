---
layout: post
title: Project Euler - Three ways
---

After solving [Path sum - two ways](https://projecteuler.net/problem=81), which was a straightforward dynamic programming problem, I began to solve the next one in the series [Path sum - three ways.](https://projecteuler.net/problem=82) After thinking about it for some minutes, I realized that at the heart of it, this was a simple graph problem in which a shortest path had to be calculated. This was a perfect job to employ Dijkstra's shortest path algorithm. I transformed the input matrix into a graph and thereafter the only modification was the addition of an additional set of two nodes, one as the source and the other was the sink. The source had an edge to all the entries in the first column with 0 cost and all the entries in the last column had edges to the sink with the cost equal to the respective entry in the matrix. 
<script src="https://gist.github.com/adijo/10126db83cbf8c6b8198.js"></script>