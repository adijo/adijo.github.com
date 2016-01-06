---
layout: post
title: Leetcode - Different Ways to Add Parentheses
---

This was a fun problem to solve. The first thing to do is to tokenize the input. Next, the basic idea is to imagine that at every operator symbol,
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

    def _forward_operate(self, num, operation, rest):
        return map(lambda x : self._evaluate(num, operation, x), rest)

    def _compute(self, curr, tokens):
        operations = set(["+", "-", "*"])
        if curr == len(tokens) - 1:
            return [int(tokens[curr])]
        elif curr == len(tokens) - 3:
            return [self._evaluate(tokens[curr], tokens[curr + 1], tokens[curr + 2])]
        elif curr < len(tokens) and tokens[curr] not in operations:
            # first option is consume.
            one = self._compute(curr + 2, tokens)

            # one contains a list.
            consume = self._evaluate(tokens[curr], tokens[curr + 1], tokens[curr + 2])
            two = self._compute(curr + 4, tokens)
            res_one = self._forward_operate(int(tokens[curr]), tokens[curr + 1], one)
            if curr + 3 < len(tokens):
                res_two = self._forward_operate(consume, tokens[curr + 3], two)
            else:
                res_two = [int(consume)]
            return res_one + res_two
        else:
            return []


    def diffWaysToCompute(self, input):
        tokens = self._tokenize(input)
        return self._compute(0, tokens) + self._compute(0, tokens[::-1])

s = Solution()
print s.diffWaysToCompute("2*3-4*5")

{% endhighlight %}