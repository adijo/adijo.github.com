---
layout: page
title: Projects
---

### CSP (Constraint Satisfaction Solver) with Arc-Consistency
An implementation of a REST based CSP solver implemented with arc-consistency. The requests are handled by a task-queue called Celery with Redis as the message broker to enable asynchronous computation.
You can view and download the code on [GitHub.](https://github.com/adijo/csp-solver-task-queues)

### Restaurant Revenue Prediction with Gradient Boosting Decision Trees
I participated in a [Kaggle](https://www.kaggle.com/c/restaurant-revenue-prediction) competition that involved the prediction of revenues for TFI. I ended up using a **Gradient Boosting Regressor** as the main algorithm for my submission and achieved a world rank of 17 out of 2257 people. Code is on [GitHub.](https://github.com/adijo/kaggle/tree/master/restaurant-revenue)

### Random sentence generator using kth order Markov Chain
Trained the model using a bunch of random jokes found on the internet. It spits out sentences like 
```
 "sure. ten miles to a thousand others break up. ""number 53!" says "i just trampling and four!".
```
Code is hosted on [GitHub.](https://github.com/adijo/markov-random-sentence-generator)

### Local Search: Hill Climbing with and without Random Restart, Simulated Annealing
Implementation of various local search algorithms to solve hard combinatorial problems such as the famous n-queens problem. Detailed description along with code and results is available on [GitHub.](https://github.com/adijo/local-search)

### Distributed Knuth Morris Pratt String Search
A toy project implementing a distributed string searching algorithm using akka and the Knuth-Morris-Pratt algorithm. The string is split into several substrings and these are subsequently searched in parallel. The algorithm will not find a match when the pattern overlaps between two split strings. Code lives on [GitHub.](https://github.com/adijo/distributed-kmp) 

### Minimax Tic-Tac-Toe Agent
Implemented a robot that will never lose in a game of tic tac toe. Implemented using a min-max algorithm on a game tree. The application works in the browser. You can try it out online [here.](https://tranquil-hamlet-6036.herokuapp.com/) Code is on [GitHub.](https://github.com/adijo/min-max-tic-tac-toe)

## Virtual Machine
A simulation of a Virtual Machine that interprets bytecode and outputs results. The code includes a sample factorial function implemented using a custom instruction set. [GitHub.](https://github.com/adijo/virtual-machine)

## Undergraduate Final Year Project:
Developed a compiler and a random forest based classification tool in Java that analyzes source code complexity and provides the probability of fault proneness in a software module.

## Data Structure Design: Partitionable Array
Designed and developed a new data structure that stores a collection of `n` elements of type `T` and supports an operation that tells you how many elements satisfy a predicate `P` and an operation that returns the index of some element that satisfies `P` in constant time. This was mentioned as one of the computer science undergraduate research
projects on Ohio state university’s page. Code is on [GitHub.](https://github.com/adijo/partitionable-array) Please see [this](http://adijo.github.io/partitionable-array/) page for a more detailed description.

## Parallelized Workflow Simulation
Using functional reactive programming constructs such as [actors](http://doc.akka.io/docs/akka/2.0/scala/actors.html) to build concurrent applications by simulating various scenarios. Current implementation includes
* An agent serving multiple requests asynchronously.
* Multiple agents serving multiple clients asynchronously with an intermediary load balancer.

Code is on [GitHub.](https://github.com/adijo/parallelized-workflow-simulation)

## Sudoku Solver using Backtracking
Solves the Sudoku puzzle. Code is on [GitHub.](https://github.com/adijo/sudoku-solver)









