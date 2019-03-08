---
layout: post
title: Rosalind - Independent Alleles
use_math: true
---


This [problem](http://rosalind.info/problems/lia/) involved more probability and less code. I really enjoy solving problems on probability and so this was a lot of fun.

### Initial thoughts

I thought this would take *a lot* of effort because there would be an exponential number of possibilities. For instance, an organism `AaBb` code mate with `AABB` or `Abab.` There are way to many possibilities and it is easy to lose track.

### Insight

The key insight is that for an organism with *any* genotype, `AaBb`, `AABB`, `aBaB`, `aaBB` and so on, the probability of producing an offspring of genotype `AaBb` **after** mating with a `AaBb` organism is exactly $0.25.$ Just work out all the possibilites and find that this is indeed true.

### Formulating a structured solution

We can thus view the birth of a `AaBb` offspring as a *success* and the birth of any other genotype a so called *failure.* At the $k^{\text{th}}$ generation, there are $2^{k}$ organisms. For each of them, the probability that they are of the desired genotype `AaBb` is $0.25.$ Thus, for $ 2^{k} $ individuals, this basically boils down to finding the probability of $ K $ successes in $ N $ trials. This is the [Binomial Distribution.](https://en.wikipedia.org/wiki/Binomial_distribution) Don't get confused with the notation, here $N$ refers to the total number of trials, which is equal to the total number of organisms at the $k^{\text{th}}$ level, which is equal to $N = 2^{k}.$ The question asks for us to find the probability that there are **at least** $n$ organisms with the desired genotype. Thus, we need to find this probability for all $ n $ in the range $[n, n + 1, ... , 2^{k}]$

In other words, in a population of $2^{k}$ individuals, first we find the probability that **exactly** $ n $ are of the desired genotype `AaBb`, then we find the probability that **exactly** $n + 1$ are of that genotype and so on until all the individuals $2^{k}$are of that genotype.

The probability of getting **exactly** $ n $ organisms of genotype `AaBb` out of $2^{k}$ is given by the binomial distribution as, with $ N = 2^{k} $: 

$$ \dbinom{N}{n} 0.25^{n} 0.75^{N - n} $$.

For the rest, we can succintly write this as

$$ \sum_{i=n}^{N} \dbinom{N}{i} 0.25^{i} 0.75^{N - i} $$.

<script src="https://gist.github.com/adijo/dcb12f1dcc9c24bdf8db.js"></script>