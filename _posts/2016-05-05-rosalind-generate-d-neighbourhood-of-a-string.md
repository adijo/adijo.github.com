---
layout: post
title: Rosalind - Generate d-neighbourhood Of A String
---
### Analysis
This [problem](http://rosalind.info/problems/ba1n/) was an implementation problem - one that required a depth first graph traversal while keeping track of what indices we have already made changes to. This way we would no repeatedly change those characters and thereby violating the constraints of the problem. I kept track of these using a `HashSet` which is a set implementation in Java.

### Code
<script src="https://gist.github.com/adijo/ba198be706a81a396a495bd52b9b4fb2.js"></script>