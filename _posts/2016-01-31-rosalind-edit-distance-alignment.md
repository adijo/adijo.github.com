---
layout: post
title: Rosalind - Edit Distance Alignment
---

Another standard algorithm [problem,](http://rosalind.info/problems/edta/) except that like the [longest common subsequence](http://adijo.github.io/2016/01/28/rosalind-finding-a-shared-spliced-motif/) problem, we were required to reconstruct the optimal alignment. For example, for the strings `ADITYA` and `ADIJO,` the edit distance is `3,` and the optimal alignment is

{% highlight python %}
ADI-JO
ADITYA
{% endhighlight %}

This requires the same technique as with the longest common subsequence problem of using the backpointer to reconstruct our optimal alignment from the memoized table.

### Code

<script src="https://gist.github.com/adijo/124fd318d8f4204ee23d.js"></script>