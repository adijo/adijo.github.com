---
layout: post
title: Rosalind - Counting Disease Carriers - Hardy Weinberg Principle
use_math: true
---

To solve this [problem,](http://rosalind.info/problems/afrq/) we need to know about the [Hardy Weinberg Principle.](https://en.wikipedia.org/wiki/Hardy%E2%80%93Weinberg_principle) I will explain this in brief.

### Hardy Weinberg Principle

*  Every diploid organism has two alleles in every chromosome. These alleles can be recessive or dominant. For example, consider the chromosome that
   contains the gene that determines eye colour. There are *variants* or *alleles* of the chromosome that is responsible for eye colour. Let us assume that the population consists of individuals with only a blue or brown colour. Let the blue *allele* be represented by $b$ and the brown allele be represented by $B.$ Then an individual, having two alleles, can have the following genotype -- $bb, BB, Bb.$
*  Let the **allele frequency of the recessive trait** be denoted by $p.$ Then the allele frequency for the dominant trait is $ q = 1 - q. $
*  Now, we know that $ p + q = 1 $ by the laws of probability. Let us expand these terms by squaring both sides:
*  $$ (p + q)^2 = 1^2 = p^2 + 2pq + q^2 = 1$$
*  What does $p^2$ equal? It is the probability of getting a homozygous recessive individual, i.e, and individual with both recessive alleles -- $bb.$ 
   Thus, $q^2$ denotes the probability of getting $BB$ and $2pq$ denotes the probability of getting $Bb.$
*  This is the Hardy Weinberg Principle. Thus, starting from the allelic frequency, we can deduce the proportion of $bb, BB, Bb$ individuals in the population. This principle has a few assumptions, *taken from Wikipedia:*
    *  organisms are diploid
    *  only sexual reproduction occurs
	*  generations are non overlapping
	*  mating is random
	*  population size is infinitely large
	*  allele frequencies are equal in the sexes
	*  there is no migration, mutation or selection

### Analysis and Solution

In our problem, we are given the proportion of homozygous recessive organisms. In other words, we are given the proportion of $bb$ organisms. Thus, we are given $p^2.$ We need to find the probability of picking an organism with **at least** one recessive allele -- The organisms with genotype $$bb$$ and $Bb.$ We already know the proportion of $bb$ individuals. We need to find the proportion of $Bb$ individuals, and this equals $2pq$ from the notes above. It boils down to simple maths now, from $p^2,$ we get $p.$ As $ p + q = 1,$ we can find $q$. We can then find $2pq$ and then we add up $p^2$ and $2pq$ to give us our final answer, $p^2 + 2pq.$ This is done for every value in our array.

### Code
<script src="https://gist.github.com/adijo/469c23af64ac64a48d82.js"></script>