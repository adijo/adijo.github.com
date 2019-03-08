---
layout: post
title: Leetcode - Serialize and Deserialize a Binary Tree

---

One way to do this [problem](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/) is to store the *preorder* and *inorder* traversals of the binary tree. This can uniquely preserve the structure of a binary tree. We still store twice the amount of data actually required although asymptotically it is still `O(n).`


An alternative to this is to serialize the tree with the following algorithm:

*  Do a level order traversal (breadth first search) of the tree.
*  While doing this, if the node is at the last level of the tree, don't add *null* nodes.
*  At any of the upper levels, if the current node does not have a left or right child node, store a *null* string to indicate this.


For example, the following tree is serialized as `[1, 2, 3, null, null, 4, 5].`
![Serialize](http://adijo.github.io/assets/leetcode_btree_serialize.png)

To deserialize a tree, we maintain two pointers. One pointer (say `i`) is to indicate which node is currently being processed. The second pointer (say `j`) is the index of the left child of `i.` There are a few corner cases to take care of. If `i` is equal to `null` we simply ignore it. If `j` is out of bounds, we simply set the left and right child of `i` as `None.`

<script src="https://gist.github.com/adijo/d9e70ce8f45dde940243.js"></script>