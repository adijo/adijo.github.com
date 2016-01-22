---
layout: post
title: Rosalind - Expected Number of Restriction Sites
use_math: true
---

Another [problem](http://rosalind.info/problems/eval/) based purely on probability and expected values.

### Analysis
The question asks us to find the expected number of times we see a string $s$ as a substring of a string of length $n$ constructed with a given GC-content.

We assign a indicator random variable $I_i$ equal to $1$ if we see the string $s$ beginning at the $i^{\text{th}}$ position. Thus, we have to find

$$ E[I_0 + I_1 + I_2 ... I_{n - 1}] = \sum_{i = 0}^{n - 1} E[I_i] $$

This is due to [Linearity of Expectation.](https://brilliant.org/wiki/linearity-of-expectation/)

The calculations of all $E[I_i]$ values are identical. Once we find the probabilities of getting symbols $G, C, T, A $ from the GC-content, we simply multiply them according the the symbols observed in $s.$

For example, if the GC-content is $0.25$, $P(G) = 0.125, P(C) = 0.125, P(A) = 0.375, P(T) = 0.375.$ Then string `AG` is constructed with probability $ 0.125 \cdot 0.375.$ Refer to [this](http://adijo.github.io/2016/01/21/rosalind-matching-random-motifs/) post to calculate the probabilities above.

Once we have the probability of randomly constructing string $ s $, the expected value of $ I_i$ is simply the expected value of a [Bernoulli trial,](https://en.wikipedia.org/wiki/Bernoulli_trial) i.e., there is a certain probability of success and failure. In our case, the success occurs if we randomly construct string $s.$ Let this expected value equal $x.$ Now, since the calculation of all $E[I_i]$ is identical, our answer is $ x \cdot (n - 1).$

### Code
<script src="https://gist.github.com/adijo/c4d3e475ee0a39797533.js"></script>

