---
layout: post
title: Rosalind - Catalan Numbers and RNA Secondary Structures
---

This [problem](http://rosalind.info/problems/cat/) took a bit of time. More than I'd have liked, anyway. I had worked out the problem correctly, although I had a bug related to where I placed the `if` conditions which caused it to malfunction. Anyway, here's how I solved it:

### Initial Thoughts

In a given RNA strand, let the starting index be `lo` and the last index be `hi.` Let us call our function `f(lo, hi).` From `lo`, consider all the places where we could have a matching. This depends on the nucleotide, `A` to `U`, `C` to `G` and the reverse. So start iterating from `lo + 1` till `hi`, and for every valid matching, say at position `i`, recursively calculate `f(lo + 1, i - 1)` and `f(i + 1, hi).` Then the total matchings are just `f(lo + 1, i - 1) * f(i + 1, hi).` 

To make the algorithm efficient, every time we calculate a value for a given `lo` and `hi,` we cache it in a dictionary. These values can then be recovered in constant time for further use. 

### Pseudocode

{% highlight python %}
f(lo, hi) = 
	accumulator = 0
	for i = lo + 1 ... hi
		if char at i is valid:
			accumulator += f(lo + 1, i - 1) * f(i + 1, hi)
	return accumulator
{% endhighlight %}

We have to take care of the various edge cases. You can see how I've done it in my code below:

<script src="https://gist.github.com/adijo/59f3c814cbc17db2506d.js"></script>