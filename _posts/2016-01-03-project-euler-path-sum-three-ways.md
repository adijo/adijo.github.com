---
layout: post
title: Project Euler - Three ways
use_math: true
---

After solving [Path sum - two ways](https://projecteuler.net/problem=81), which was a straightforward dynamic programming problem, I began to solve the next one in the series [Path sum - three ways.](https://projecteuler.net/problem=82) After thinking about it for some minutes, I realized that at the heart of it, this was a simple graph problem in which a shortest path had to be calculated. This was a perfect job to employ Dijkstra's shortest path algorithm. I transformed the input matrix into a graph and thereafter the only modification was the addition of an additional set of two nodes, one as the source and the other was the sink. The source had an edge to all the entries in the first column with 0 cost and all the entries in the last column had edges to the sink with the cost equal to the respective entry in the matrix. 

{% highlight python %}
import heapq
import time

f = open("data/p81.txt", "r")
matrix = []
for line in f:
    row = map(int, line.split(","))
    matrix.append(row)


class Solver(object):

    def _is_valid(self, matrix, i, j):
        return 0 <= i < len(matrix) and 0 <= j < len(matrix[0])

    def _construct_graph(self, matrix):
        graph = {}
        for i in xrange(len(matrix)):
            for j in xrange(len(matrix[0]) - 1):
                graph[(i, j)] = {}
                if self._is_valid(matrix, i + 1, j):
                    graph[(i, j)][(i + 1, j)] = matrix[i][j]
                if self._is_valid(matrix, i - 1, j):
                    graph[(i, j)][(i - 1, j)] = matrix[i][j]
                if self._is_valid(matrix, i, j + 1):
                    graph[(i, j)][(i, j + 1)] = matrix[i][j]

        # source
        graph[(-1, -1)] = {}
        # make connections for source
        # first column.
        for i in xrange(len(matrix)):
            graph[(-1, -1)][(i, 0)] = 0

        # sink
        graph[(-2, -2)] = {}
        # make connections from last column to sink
        for i in xrange(len(matrix)):
            graph[(i, len(matrix[0]) - 1)] = {}
            graph[(i, len(matrix[0]) - 1)][(-2, -2)] = matrix[i][len(matrix[0]) - 1]

        return graph


    def dijkstra(self, graph):
        queue = []
        distance = {}
        distance[(-1, -1)] = 0
        for node in graph[(-1, -1)]:
            distance_to_node = graph[(-1, -1)][node]
            heapq.heappush(queue, (distance_to_node, node))
        
        while (-2, -2) not in distance:
            dist, top = heapq.heappop(queue)
            if top not in distance:
                distance[top] = dist
                for node in graph[top]:
                    new_dist = distance[top] + graph[top][node]
                    heapq.heappush(queue, (new_dist, node))
        return distance[(-2, -2)]


    def solve(self, matrix):
        graph = self._construct_graph(matrix)
        return self.dijkstra(graph)


s = Solver()
start = time.time()
print s.solve(matrix)
print time.time() - start
{% endhighlight %}