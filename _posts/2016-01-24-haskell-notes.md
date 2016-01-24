---
layout: post
title: Haskell Notes
---

## Notes for [CIS 194](http://www.seas.upenn.edu/~cis194/)

<p class="message">
  The following notes are snippets taken out of the [Introduction to Haskell](http://www.seas.upenn.edu/~cis194/) class offered by UPenn.
</p>

### Parametric Polymorphism

*  The **caller gets to pick the types.** 
*  All Haskell functions must be parametric in their type parameters; the functions must not care or make decisions based on the choices for these parameters. A function can’t do one thing when a is `Int` and a different thing when a is `Bool.` This property is called *parametricity.*
*  There are many deep and profound consequences of parametricity. One consequence is something called type erasure. Because a running Haskell program can never make decisions based on type information, all the type information can be dropped during compilation. Despite how important types are when writing Haskell code, they are completely irrelevant when running Haskell code. This property gives Haskell a huge speed boost when compared to other languages, such as Python, that need to keep types around at runtime. 
*  Total and partial functions - Functions that crash on some inputs or recurse infinitely are called partial functions. Functions that are defined for all input types are total functions. Partial functions should be avoided.
*  Common recursion patterns - `map, filter, fold.`

