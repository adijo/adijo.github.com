---
layout: post
title: Project Euler - Dice Game
---

### Analysis

The [problem](https://projecteuler.net/problem=205) seemed straightforward -- we need to enumerate all the outcomes for Pete and Colin and find out all the 2-tuples for each value in Pete and Colin's possible outcomes. Since each of these 2-tuples are equally likely, we count the number of the number of times Pete has a value higher than Colin. This value divided by the total number of 2-tuples will give us the answer. 

A recursive method does a fine job of enumerating outcomes of the sum on the `n` faced dice after rolling it `t` times.

### Brute Force

The brute force method is the following

{% highlight python %}
pete = enumerate all possible sums for a 4-faced dice after rolling 9 times.
colin = enumerate all possible sums for a 6-faced dice after rolling 6 times.
acc = 0
for p in pete:
	for c in colin:
		if p > c:
			acc += 1

print float(acc) / (len(pete) * len(colin))
{% endhighlight %}

This naive approach is quite expensive, it has `12230590464` iterations and takes a lot of time.

### Binary Search

We could sort the arrays and binary search for the smallest value in Pete's array such that it is greater than a given value (taken from Colin's array). We do this for every value in Colin's array. Once we find the smallest greater number, we can easily find the number of numbers greater than the given value (since the array is sorted). This approach saves us a lot of time and has only about `839808` iterations. 

<script src="https://gist.github.com/adijo/e3f848c610dce18dbf39.js"></script>

