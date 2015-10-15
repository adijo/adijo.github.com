---
layout: page
title: Projects
---

## CSP (Constraint Satisfaction Solver) with Arc-Consistency
An implementation of a REST based CSP solver implemented with arc-consistency. The requests are handled by a task-queue called Celery with Redis as the message broker to enable asynchronous computation.
You can view and download the code on [GitHub.](https://github.com/adijo/csp-solver-task-queues)

## Restaurant Revenue Prediction with Gradient Boosting Decision Trees
I participated in a [Kaggle](https://www.kaggle.com/c/restaurant-revenue-prediction) competition that involved the prediction of revenues for TFI. I ended up using a **Gradient Boosting Regressor** as the main algorithm for my submission and achieved a world rank of 17 out of 2257 people. Code is on [GitHub.](https://github.com/adijo/kaggle/tree/master/restaurant-revenue)

## Random sentence generator using kth order Markov Chain.
Trained the model using a bunch of random jokes found on the internet. It spits out sentences like 
```python
 "sure. ten miles to a thousand others break up. ""number 53!" says "i just trampling and four!".
```
Code is hosted on [GitHub.](https://github.com/adijo/markov-random-sentence-generator)

## Local Search: Hill Climbing with and without Random Restart, Simulated Annealing.
Implementation of various local search algorithms to solve hard combinatorial problems such as the famous n-queens problem. Detailed description along with code and results is available on [GitHub.](https://github.com/adijo/local-search)

## Distributed Knuth Morris Pratt String Search
A toy project implementing a distributed string searching algorithm using akka and the Knuth-Morris-Pratt algorithm. The string is split into several substrings and these are subsequently searched in parallel. The algorithm will not find a match when the pattern overlaps between two split strings. Code lives on [GitHub.](https://github.com/adijo/distributed-kmp)  $1 + 2$ 





