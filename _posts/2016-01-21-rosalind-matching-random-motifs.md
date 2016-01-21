---
layout: post
title: Rosalind - Matching Random Motifs
use_math: true
---

This [problem](http://rosalind.info/problems/rstr/) was purely based on probability.

### Analysis
The GC-content of the protein is given to us, call it $ \text{GC.} $ We can find the probability of `G` and `C` characters as $ \dfrac{\text{GC}}{2}. $ For `A` and `T`, this value is $ \dfrac{1 - \text{GC}}{2}. $

Thus, let $P(G) = g, P(C) = c, p(A) = a, P(T) = t.$

The probability of getting a string equal to a given one is equal to the multiplication of the probabilities of all the symbols in the string. For a string `ATGCT`, the probability of randomly constructing that string - with the probabilies given as above - is $a \cdot t \cdot g \cdot c \cdot t.$

In our problem there are $ N $ trials in which random strings are constructed. We have to find the probability of **at least** one of them being equal to our string $s.$

$$ P(\text{at least one string equals s}) = 1.0 - P(\text{no string equals s}) $$

For a given string $s$, we first find the probability of **not** obtaining it if it is randomly constructed using the given probabilities. Let this be $p.$ Thus, the probability that we do not get $s$ even once in $N$ trials is $p^N$. Hence, the probability of getting it **at least once** is $ 1.0 - p^N. $

### Code
<script src="https://gist.github.com/adijo/1ec0e9951bd1d274f4d1.js"></script>