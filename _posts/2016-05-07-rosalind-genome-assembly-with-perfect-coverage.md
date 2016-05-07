---
layout: post
title: Rosalind - Genome Assembly with Perfect Coverage
---

Today's [problem](http://rosalind.info/problems/pcov/) required a combination of several techniques. First, we needed to construct a [De Bruin](https://en.wikipedia.org/wiki/De_Bruijn_graph) graph. Second, we had to find a Hamiltonian circuit and finally, build a KMP (Knuth-Morris-Pratt) prefix table to reduce our result into the final required answer.

### Analysis
*  The problem mentioned that there was one distinct simple cycle in the De Bruin graph. This made it obvious that we had to find a Hamiltonian circuit (find a path that starts and finishes at the same node such that each node in the graph is visited exactly once). Once we found a path, we had to combine it to a single string which was done as follows:
For a path `[ACCC, CCCT, CCTG]`, we take the first string and then append the last character of every other string from index `1.` This path is not Hamiltonian, it is just to explain how the path is merged. 
*  After running my code against the sample input, I noticed that my output
is longer than the expected answer. After a few minutes of looking at my answer, I noticed that since the strings are circular, they wrap around after the end. Hence some part of the suffix was excessive as it was equivalent to the prefix. Now we use the KMP algorithm to build a prefix table to find the longest prefix which is also a suffix of the string. We could have done this in a brute force manner as well. Building a KMP table can be complicated to explain, but I recommend watching [this](https://www.youtube.com/watch?v=KG44VoDtsAA) video.
*  And that's it, after we find the length of the longest prefix which is also a prefix, we trim those many characters from the previous step and return the new string.



### Code
<script src="https://gist.github.com/adijo/6f363fe19ab27344815a2fcdec738eef.js"></script>

