---
layout: post
title: Optimization - Fantasy Football League 
use_math: true
---

Some of my friends play a lot of [FPL.](http://fantasy.premierleague.com/) One of them asked me an interesting problem. Out of the existing players, he wanted to choose 4 players, a defender, two midfielders and one forward such that he would get maximum expected points within a budget.

### Analysis
This sounded suspiciously a lot like the knapsack problem. Each player $ p_i $ had an expected profit $ p_i $ and a cost of $ c_i.$ Let the budget be $ B.$ To solve this problem, I realised that we could formulate an integer linear program. We denote an indicator variable $ x_i $ for each player which could take on values of $ {0, 1}. $ Thus, we needed to maximize the following quantity, where $ n $ denotes the number of players.

$$ x_1 \cdot p_1 + x_2 \cdot p_2 + x_3 \cdot p_3 + \cdots + x_n \cdot p_n = \sum_{i = 1}^n x_i \cdot p_i $$  

To enforce the condition that we need only a certain amount of midfielders, forwards and defenders, we associate each indicator variable $ x_i $ with a particular class of player. We then add constraints as follows. In our dataset, let us assume that players $ x_i \in \[1 \cdots p\] $ are defenders, $ x_i \in \[p + 1 \cdots k\] $ are midfielders and $ x_i \in \[ k + 1 \cdots n \] $ are forwards. We add constraints to this as follows.

$$ \sum_{i = 1}^p x_i = 1 $$

because out of the $ p $ defenders, we only want $ 1. $

For the midfielders,

$$ \sum_{i = p + 1}^k x_i = 2 $$

as we need $2$ defenders.

Finally,

$$ \sum_{i = k + 1}^n x_i = 1 $$

for $ 1 $ forward.

The final constraint is that the sum of the cost of the chosen players should not exceed the budget.

$$ x_1 \cdot c_1 +  x_2 \cdot c_2 + x_3 \cdot c_3 + \cdots + x_n \cdot c_n \leq B $$

To summarize, here is the full linear program.

$$ \text{Maximize} \sum_{i = 1}^n x_i \cdot p_i $$

with constraints

$$ \sum_{i = 1}^p x_i = 1 $$

$$ \sum_{i = p + 1}^k x_i = 2 $$

$$ \sum_{i = k + 1}^n x_i = 1 $$

$$ \sum_{i = 1}^n x_i \cdot c_i \leq B $$


Thus, we have formulated our integer linear program. To solve this in python, I used the [PuLP](https://pythonhosted.org/PuLP/) module. Our `Solver` module expects an array of players, where each player is defined as a `5-tuple` of `(name, utility, cost, position, team).` The `utility` part is interesting, and was obtained online from various sources as the expected future utility of the player. This can be an interesting machine learning project itself, predicting the expected utility of a player, something that I will look into in the future. The number of each type of players is parameterized and can be set as desired. 

### Code

<script src="https://gist.github.com/adijo/00ac1c350822c34ff7b7.js"></script>




