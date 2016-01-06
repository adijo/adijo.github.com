---
layout: post
title: Leetcode - Different Ways to Add Parentheses
---

This was a fun [problem](https://leetcode.com/problems/different-ways-to-add-parentheses/) to solve. The first thing to do is to tokenize the input. Next, the basic idea is to imagine that at every operator symbol,
what would happen if this operation was carried out last? We define the function `compute(lo, hi)` that will 
return a list of all possible values by adding all possible parentheses. The algorithm is as follows - We loop from `lo` to `hi` inclusive
and if we find an operator (+, - or *) at position `i`, we split the list into two parts - the sublist to the left of this operator and the sublist to the right. 
We recursively find `compute(lo, i - 1)` and `compute(i + 1, hi)`. We carry out the 
operation at position `i` for every entry in the cartesian product of these two lists.

It is better understood by this visualization and by the code.

![Parentheses](http://adijo.github.io/assets/leetcode_parens.png)

The left list `[6]` and right list `[20]` could have multiple elements and the operation is a cartesian product of these two lists with the respective operator, which in this case is the subtraction symbol.

Another fun feature in my code below was the use of mapping operators to functions with a dictionary. This is done in the `_evaluate` function. 

{% highlight python %}
class Solution(object):
    def _tokenize(self, string):
        tokens = []
        i = 0
        operators = set(["+", "-", "*"])
        while i < len(string):
            char = string[i]
            if char in operators:
                tokens.append(char)
                i += 1
            else:
                # find the number
                j = i + 1
                while j < len(string):
                    if string[j] not in operators:
                        j += 1
                        continue
                    else:
                        tokens.append(str(int(string[i:j])))
                        break
                if j >= len(string):
                    tokens.append(str(int(string[i:])))

                i = j        
        return tokens


    def _evaluate(self, one, operation, two):
        mapping = {

            "+" : lambda x, y : int(x) + int(y),
            "-" : lambda x, y : int(x) - int(y),
            "*" : lambda x, y : int(x) * int(y)
        }

        f = mapping[operation]
        return f(one, two)

    def _is_operation(self, char):
        operations = set(["+", "-", "*"])
        return (char in operations)

    def _compute(self, tokens, lo, hi):
        
        if lo == hi:
            return [int(tokens[lo])]
        elif lo < hi:
            answer = []
            for i in xrange(lo, hi + 1):
                if self._is_operation(tokens[i]):
                    # [lo .. i - 1, i + 1 .. mid]
                    less = self._compute(tokens, lo, i - 1)
                    more = self._compute(tokens, i + 1, hi)
                    for l in less:
                        for m in more:
                            answer.append(self._evaluate(l, tokens[i], m))
            return answer



    def diffWaysToCompute(self, input):
        tokens = self._tokenize(input)
        return self._compute(tokens, 0, len(tokens) - 1)

s = Solution()
print s.diffWaysToCompute("2*3-4*5")


{% endhighlight %}