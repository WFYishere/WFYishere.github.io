---
title: 'Competitive Programming 4 Notes'
date: 2025-03-01 14:59:01
categories: [CompetitiveProgramming, Notes]
tags: [Notes, CompetitiveProgramming]
mathjax: true
code_block_shrink: false
---

Notes for [Competitive Programming 4](https://cpbook.net/). A very good book.

<!--more-->

# Foreword

This post are some notes that I have taken from the book CP4. Do note that it is much better if you read the book by yourself and these are just study notes that I have made. I didn't make notes for all chapters, and the arrangement of this study note might be different from the ordering of chapters in the book. I have also included my study plan at the end of the post.

# Chapter 1: Introduction

## Algorithm Analysis

1. Modern Computers process $\approx 100M$ operations per second. Use these to approximately estimate whetehr your algorithm is fast enough.

2. Approximations

- $ 10! \approx 3 \times 10^6 $
- 32-bit signed integers (`int`) and 64-bit signed integers (`long long`) have upper limits of  $2^{31}-1 \approx 10^9$, $2^{63}-1 \approx 10^{18}$

3. Estimating Time Complexity

| $n$        | Worst AC Algorithm        |
|------------|--------------------------|
| $\leq [10..11]$ | $O(n!), O(n^6)$ |
| $\leq [17..19]$ | $O(2^n \times n^2)$ |
| $\leq [18..22]$ | $O(2^n \times n)$ |
| $\leq [24..26]$ | $O(2^n)$ |
| $\leq 100$ | $O(n^4)$ |
| $\leq 450$ | $O(n^3)$ |
| $\leq 1.5K$ | $O(n^{2.5})$ |
| $\leq 2.5K$ | $O(n^2 \log n)$ |
| $\leq 10K$ | $O(n^2)$ |
| $\leq 200K$ | $O(n^{1.5})$ |
| $\leq 4.5M$ | $O(n \log n)$ |
| $\leq 10M$ | $O(n \log \log n)$ |
| $\leq 100M$ | $O(n), O(\log n)$ |


## Testing Your Code

1. Use `fc` to tell the difference between your code and sample code, instead of manually checking.
- `program.exe < in.txt > myout.txt`
-  `fc myout.txt out.txt`

2. For problems with multiple test cases in a single run , include two identical sample test cases consecutively in the same run to check if there are variables that are not resetted properly.

3. Include Corner Cases like `N=0` or `N=1` or negative values and large values out of bound of `int` 

2. refrain from coding until you are sure that your algorithm is both correct and fast enough

# Study Plan

1. Week 1: Getting Started with CP + Speed Boost
    - Chapters: 1.3, 1.4, 2.2.1 & 2.2.2
    - Understanding Competitive Programming & Contest Mindset
    - Basic Sorting, Brute Force, Implementation
    - Fast coding & debugging skills
