---
layout: post
title: Rosalind - Introduction to Pattern Matching - Implementing a Trie
---

The [problem](http://rosalind.info/problems/trie/) basically asks us to implement a [trie.](https://en.wikipedia.org/wiki/Trie) I did this in Python.

### Representation

Every node of the trie is represented as a dictionary. The keys associated with the dictionary are alphabets of the inserted word at that depth. The value associated with the respective key is a tuple of a dictionary (which is just the node associated with that alphabet; the next node further down the trie) and a boolean (except in the case of `id`, which is just a single value). The dictionary also has a special `id` character which is just the identifier associated with the particular node, which is required for the current question. 

As a practical example, if we insert the following strings, `ATAGA, ATC, GAT`, our trie will look like this:

{% highlight python %}
{'A': ({'id': 2, 'T': ({'A': ({'id': 4, 'G': ({'A': ({'id': 6}, True), 'id': 5}, None)}, None), 'C': ({'id': 7}, True), 'id': 3}, None)}, None), 'id': 1, 'G': ({'A': ({'id': 9, 'T': ({'id': 10}, True)}, None), 'id': 8}, None)}
{% endhighlight %}

### Code
<script src="https://gist.github.com/adijo/86d0f6a7b85cf2dc4d80.js"></script>