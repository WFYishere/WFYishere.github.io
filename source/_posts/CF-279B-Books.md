---
title: '[CF] 279B - Books'
date: 2025-01-27 21:17:16
categories: [CompetitiveProgramming, CodeForces, ProblemSet]
tags: [BruteForce, CPP]
code_block_shrink: false
---

Easy question but I thought of it in a too difficult way.

<!--more-->

### My Solution

**Idea**: Notice that for each `i`th book, we just need to find `r_i` such that the sum of the time from `i` to `r_i`th book is smaller than `t`. We can also notice that r_i is not descending, so each time we calculate `r_i` from `r_{i-1}`

```cpp
```

### Official Solution

Similar Idea but [much more descent code](https://codeforces.com/blog/entry/95148).

### Thoughts

You shouldn't solve a question from strange or fancy techniques. Try solving a question from the most bruteforce way and gradually decrease the question.