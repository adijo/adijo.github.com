---
layout: post
title: Leetcode - Different Ways to Add Parentheses
---

This was a fun [problem](https://leetcode.com/problems/different-ways-to-add-parentheses/) to solve. The first thing to do is to tokenize the input. Next, the basic idea is to imagine that at every operator symbol,
what would happen if this operation was carried out last? We define the function `compute(lo, hi)` that will 
return a list of all possible values by adding all possible parentheses. The algorithm is as follows - We loop from `lo` to `hi` inclusive
and if we find an operator (+, - or *) at position `i`, we split the list into two parts - the sublist to the left of this operator and the sublist to the right. 
We recursively find `compute(lo, i - 1)` and `compute(i + 1, hi)`. We carry out the 
operation at position `i` for every entry in the cartesian product of these two lists.

It is better understood by this visualization and by the code.

![Parentheses](http://adijo.github.io/assets/leetcode_parens.png)

The left list `[6]` and right list `[20]` could have multiple elements and the operation is a cartesian product of these two lists with the respective operator, which in this case is the subtraction symbol.

Another fun feature in my code below was the use of mapping operators to functions with a dictionary. This is done in the `_evaluate` function. 

<script src="https://gist.github.com/adijo/9d6c1b687434a4462c47.js"></script>