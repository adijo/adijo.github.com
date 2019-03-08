---
layout: post
title: Leetcode - Bulb Switcher
use_math: true
---

I solved this [problem](https://leetcode.com/problems/bulb-switcher/) by trying to find patterns in the output for various input values. 


### Analysis
At first, I tried the naive approach, that is for each index, I found out the number of indices that would toggle this particular bulb. Depending on this parity, we can find out the final answer. This was too slow to get accepted by the judge. I thought about it for some time but couldn't come up with anything. I decided to try to detect patterns in the output for each input value. And sure enough, a pattern emerged. With $ n $ referring to the number of bulbs, the number of bulbs on after $ n $ rounds of toggling carried out in the way described in the question were as follows.


{% highlight python %}
1 : 1
2 : 1
3 : 1
4 : 2
5 : 2
6 : 2
7 : 2
8 : 2
9 : 3
10 : 3
11 : 3
12 : 3
13 : 3
14 : 3
{% endhighlight %}

The number of `1's` here equaled `3,` the number of `2's` equaled 5 and so on. From here, after fiddling with the sequence, I decided to enumerate the sequence above.

{% highlight python %}
1 : 3
2 : 5
3 : 7
4 : 9
5 : 11
{% endhighlight %}

What this means is that the first three values of $n$ would have $ 1 $ bulb on, the next $ 5 $ values of $ n $ would have $ 2 $ bulbs on and so on. We have a sequence as follows, $ 1, 1, 1, 2, 2, 2, 2, 2, 3, 3, 3, 3, 3, 3, 3 \cdots $ Given a particular $ n, $ we need to be able to quickly find its *index.*  We can find out the cumulative sum of the above sequence as follows

{% highlight python %}
1 : 3
2 : 8
3 : 15
4 : 24
{% endhighlight %}

Thus, given a value of $ n $, if we can quickly find out its index in the above table, we can find the number of bulbs on. The sequence above can be written with the following recurrence relation.

$$ f(0) = 3, f(n) = 2(n + 1) + 1 + f(n - 1) $$

If we [solve](http://www.wolframalpha.com/input/?i=f%280%29+%3D+3%2C+f%28n%29+%3D+%282*%28n+%2B+1%29+%2B+1%29+%2B+f%28n+-+1%29) this recurrence relation, we get a closed form solution for $ n, $ which is $f(n) = n^2 + 4n + 3.$ Thus, for any given value of $ n, $ we can find the positive root of this quadratic equation and after adjusting it by $ 1 $ for the indices, return that value. For example, if we need to find the number of bulbs on for $n = 10$, we have

$$ n^2 + 4n + 3 = 10$$

After find out the roots using $ a = 1, b = 4, c = -7 $ in the quadratic formula, $ \dfrac{-b + \sqrt{b^2 - 4ac}}{2a}, $ we get $ n = 1.31662479036. $ We find the ceil, $ \text{ceil}(1.3166) = 2 $ and then do the off by $ 1 $ adjustment by adding $ 1, $ which gives us our final answer, $ 3. $

### Code
<script src="https://gist.github.com/adijo/04583f051a7bbdb651e4.js"></script>