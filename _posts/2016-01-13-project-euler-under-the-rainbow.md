---
layout: post
title: Project Euler - Under the Rainbow
use_math: true
---

No code required for [this](https://projecteuler.net/problem=493) one. I really enjoyed solving it though. 

### Linearity of Expectation - The Holy Grail

Many problems can be simplified by the somewhat suprising fact that

$$ E[X_1 + X_2 + X_3] = E[X_1] + E[X_2] + E[X_3] $$

This is called the [Linearity of Expectation](https://brilliant.org/wiki/linearity-of-expectation/) and it fascinates me everytime.

### Initial thoughts

According to my intuition, this problem was an application of the property of linearity of expectation. The question was -- what factor should I attach the indicator random variable to?

*  *Could it be $1$ if we see a distinct colour on trial $i?$* No, that doesn't make sense.
*  *Is it like the Coupon Collector's Problem?* Nope, that wouldn't work.
*  *Since there are a limited number of colours, we could assign $1$ if we saw that particular colour and $0$ otherwise. This could be extended to find the expected value of distinct colours.* **Yes!** 

### Solution

Let $ I_0 $ be the random variable that equals $ 1 $ if we see the $ 0^{\text{th}} $ colour **at least** once in $ 20 $ trials and $ 0 $ otherwise.

The expected value of this can be described by the [Hypergeometric distribution.](https://en.wikipedia.org/wiki/Hypergeometric_distribution)

$$ E[I_0] = 1 \cdot P(\text{colour is seen at least once}) + 0 \cdot P(\text{doesn't matter}) $$

$$ E[I_0] = 1 \cdot (1 - P(\text{colour is never seen})) $$

The probability that the colour is never seen can be simplified using the formula for finding $ k $ successes in $ n $ draws, *without replacement*, from a finite population size $ N $ that contains exactly $ K $ successes. To fit our problem, let us define success as seeing one of the other colours and not colour $ 0. $ Thus, we get $ N = 70, K = 60, n = 20, k = 20 $. According to the formula, the answer is given by 
$$ \dfrac{\dbinom{K}{k} \dbinom{N - K}{n - k}}{\dbinom{N}{n}} $$

Substituting our numbers, we get

$$ \dfrac{\dbinom{60}{20} \dbinom{70 - 60}{0}}{\dbinom{70}{20}} = 0.02589402828$$

But remember, this is the probability that we never see our colour. The probability of seeing it **at least** once is $ 1 - 0.02589402828 = 0.97410597171.$

Thus, $E[I_0] = 0.97410597171 $.

The same is true for $E[I_1], E[I_2] ... E[I_6] $.

What we need is $E[I_0 + I_1 + ... + E[I_6]] $ which equals $ E[I_0] + E[I_1] + ... E[I_6] $ due to linearity of expectation as discussed earlier.

This equals $ 0.97410597171 * 7 = \underline{6.818741802.}$

