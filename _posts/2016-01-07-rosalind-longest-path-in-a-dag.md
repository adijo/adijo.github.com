---
layout: post
title: Rosalind - Longest Path in a Directed Acyclic Graph
---

The mention of *longest* or *shortest* usually hints towards a dynamic programming solution and this [problem](http://rosalind.info/problems/ba5d/) was no different. One way to think about the problem is the following: We start backwards, from the sink. The longest path from the sink to the sink is 0. Ok, that was obvious. Next, consider all the incoming edges to this node.
The longest path to the sink is the maximum of all these edges. Then we recursively calculate the value for all previous nodes until we reach the source. However to solve this problem I have written the code to work forward - The search begins at the source. This will be clearer after looking at the code. The actual search is carried out by the `compute` function. The `longest_path` dictionary is to cache results. The `longest_path_choice` stores which choice we need to make from the given node to maximize the distance to the sink.

<script src="https://gist.github.com/adijo/e5332bbd459723972c4a.js"></script>