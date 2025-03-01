---
title: '[CF] 189A - Cut Ribbon'
date: 2025-01-24 22:28:57
categories: [CompetitiveProgramming, CodeForces, ProblemSet]
tags: [DynamicProgramming, CPP]
code_block_shrink: false
---

A simple dynamic programming question.

<!--more-->

### My Solution

Simply use dynamic programming. use dp[i] to indicate the maximum number of pieces for lenth i. The fromula would be `dp[i] = 1 + max({dp[i-a], dp[i-b], dp[i-c]})`


**Idea**: 

```cpp
#include <iostream>
#include <cstring>
#include <algorithm>
using namespace std;
int n, a, b, c;
int dp[4001] = {0};

int piece(int len) {
    if (len == 0) {
        return 0;
    }
    if (len < 0) {
        return -8000;
    } 
    if (dp[len] != 0) {
        return dp[len];
    }
    
    dp[len] = max({piece(len-a), piece(len-b), piece(len-c)}) + 1;
    return dp[len];
}

int main()
{
    scanf("%d%d%d%d", &n, &a, &b, &c);

    int arr[] = {a, b, c}; 
    sort(arr, arr + 3);
    a = arr[0];
    b = arr[1];
    c = arr[2];

    printf("%d", piece(n));
}
```

### Official Solution

The problem is to maximize x+y+z subject to ax+by+cz=n. Constraints are low, so simply iterate over two variables (say x and y) and find the third variable (if any) from the second equation. Find the maximum over all feasible solutions.

Or use DP.

Probably bruteforce takes less space, time complexity for DP is `O(n / a)`, for bruteforce is the same.

### Thoughts

Easy DP question.