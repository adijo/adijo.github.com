---
layout: post
title: Leetcode - House Robber III
use_math: true
---

This [one](https://leetcode.com/problems/house-robber-iii/) was a standard dynamic programming on a tree problem.

### Analysis

Some key observations were:

*  If we rob a node, we cannot rob its children.
*  If we do not rob a node, we *can* rob *both* its children.

Thus, we maintain a state $dp(\text{node}, \text{flag})$ that indicates the maximum value that we can rob for a tree rooted at this $\text{node}$ with a particular $\text{flag}.$ Thus, our transitions are as follows.

For a state `dp[node][flag],`

`if flag is true`
```dp[node][flag] = dp[node.left][false] + dp[node.right][false]```

`if flag is false`
```dp[node][flag] = max(dp[node.left][false] + dp[node.right][false], 
					dp[node.left][true] + dp[node.right][true] + node.val)```

### Code
<script src="https://gist.github.com/adijo/557107228e95f7dea9b2e180b7829db1.js"></script>
