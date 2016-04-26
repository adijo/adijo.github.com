---
layout: post
title: Rosalind - Global Alignment with Constant Gap Penalty
---

This [problem](http://rosalind.info/problems/gcon/) was a variant of [this](http://rosalind.info/problems/glob/) problem.

### Analysis

*  Some state had to be maintained to indicate that there had been a previous contiguous gap that had been inserted in each string. This can be done by introducing a boolean flag which is `1` if there was a gap just before this character and `0` otherwise for string `s`. Similarly, there is another boolean flag for string `t.`
*  Thus, instead of a 2D dynamic programming state, we use a 4D state which is defined as follows: `dp[i][j][gapS][gapT]`
*  This gives us the maximum alignment for strings (in python notation) `s[:i+1]` and `t[:j+1]` with gap states `gapS` and `gapT.` There are initially set to `false` because while starting from the right of the strings, there are no previous contiguous gaps introduced.
*  Now, for any given state with parameters `i, j, gapS, gapT,` if `gapS` is `true,` this means that we have already levied a gap penalty for this state and therefore while introducing another gap, no penalty should be levied. The same is true for `gapT.` The state transitions are clearer after looking at my highly (ahem) verbose java code.
*  For the Blosum65 scoring matrix, I generated this by parsing a Blosum65 text file that looked like this:

<script src="https://gist.github.com/adijo/bd6672f6eac212294004e3a68f4e62ad.js"></script>

*  I like the idea of using code to generate code, so I wrote a python script that reads this file and generates some Java code that populates a class that exposes a static `getScore(a, b)` method which gives you the Blosum65 score for characters `a` and `b.` Now this piece of code just generates the `HashMap` but you can also generate the entire Java class.

<script src="https://gist.github.com/adijo/1eb53b2bb3e0a3bcb70e55c7c4ad5986.js"></script>

### Code

Now for the actual Java code, which is organised into two classes that I wrote and one separate class that parses fasta.

#### Blosum65.java

<script src="https://gist.github.com/adijo/f60725e3928e1f059634d4793d463c32.js"></script>

#### FastaSequence.java
<script src="https://gist.github.com/adijo/7e81ec8a67d612a0ea515090ab92419f.js"></script>

#### Main.java

<script src="https://gist.github.com/adijo/ede2e6a044069dac2d8197b9ce0c02be.js"></script>



