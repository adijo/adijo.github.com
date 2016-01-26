---
layout: post
title: Rosalind - Finding a Spliced Motif
---

This [problem](http://rosalind.info/problems/sseq/) was fun to solve. Briefly, for a string `s,` we needed to find the indices where it occurs as a subsequence in string `t.`

### Analysis
*  This problem could be done by brute force, first finding the positions were characters in `s` occur. Then for each of these index array, try all possible combinations. For example, if string `t = ACGTAA,` the index array would be 

{% highlight python %}
A = [1, 5, 6]
C = [2]
G = [3]
T = [4]
{% endhighlight %}

We then find all possible candidates from these character arrays in the order the characters occur in `s.`

This is quite inefficient.

*  We could instead use **binary search** since the index arrays are sorted. For every character in `s,` we find the smallest index in a particular index array that is after a particular given index. This is clearer with an example.

If `s = ACGTACGTGACG` and `t =  GTA,` the index arrays for string `t` are

{% highlight python %}
'A': [0, 4, 9] 
'C': [1, 5, 10] 
'T': [3, 7] 
'G': [2, 6, 8, 11]
{% endhighlight %}

Now we iterate through the characters of `s` one by one, considering the respective index array for the character encountered. For the first character in `t`, that is `G`, the corresponding index array is `[2, 6, 8, 11].` We find the *smallest* index here greater than `-1,` which is the first initialization. Let this index be equal to `i.` Now for character `T,` the index array is `[3, 7].` Here we find the smallest index that is greater than `i.` We then update `i` to be this new value and continue in our search. This is how the answer can be calculated efficiently.

### Code
<script src="https://gist.github.com/adijo/97a049b22ce3eda8aa11.js"></script>