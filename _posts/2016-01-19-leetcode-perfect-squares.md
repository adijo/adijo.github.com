---
layout: post
title: Leetcode - Perfect Squares
---

This [problem](https://leetcode.com/problems/perfect-squares/) required a couple of insights. I initially coded the solution in Python but could not get it accepted even though the time complexity seemed reasonable to me. I had to re-do it in Java and that worked. That was actually a good thing since I finally wrote some Java code after several weeks.

### Analysis and Algorithm
*  Since we have to find the minimum number of perfect squares to make up a number, we would need to enumerate the perfect squares. One insight is that we don't need to 
   enumerate more than `sqrt(n)` numbers. All the numbers after `sqrt(n)` will have a square higher than our given number. 

*  The second part is relatively simple, we use the signature dynamic programming technique. Looking at the list of perfect squares from the right end, we could either use
   this particular number to reduce our problem to `n - candidates[index]` or we could move on to the second last index. These are the only two cases. We consider both and thus formulate our recurrence relation as follows. We define `dp[n][index]` to be the minimum number of perfect squares required to get `n` if only numbers from `[0 ... index]` are allowed to be taken. Note that `candidates` is the list of perfect squares that we found out from the first step.
   {% highlight python %}
    dp[n][index] = min(1 + dp[n - candidates[index]][candidates.size - 1], dp[n][index - 1])
   {% endhighlight %}

As a concrete example, consider the case of number `13.` The candidates for this case are `[1, 4, 9].`
{% highlight python %}
dp[13][2] = min(1 + dp[13 - 9][2], dp[13][2])
{% endhighlight %}

### Notes

I spent around 10 minutes trying to debug my solution in Java. While writing a top down recursive program, I often handle the boundary cases after making the function call. In this particular case I was returning `Integer.MAX_INTEGER` if I came across an invalid argument. After this was incremented by 1, as it is in our algorithm, it caused an overflow. Having used Python for the past few weeks the possibility of overflow didn't occur to me for 10 minutes. Anyway, I'll keep that in mind for the future.


### Code
<script src="https://gist.github.com/adijo/7679d78b4b3808521469.js"></script>