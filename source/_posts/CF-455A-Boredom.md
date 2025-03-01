---
title: '[CF] 455A - Boredom'
date: 2025-01-26 13:32:07
categories: 
- [CompetitiveProgramming, CodeForces, ProblemSet]
- [Unsolved]
tags: [DynamicProgramming, CPP]
code_block_shrink: false
---

I thought of a different approach to the question, not sure if it will work. 

<!--more-->

### My Solution

**Idea**: The final score that we get = `sum - sum_deleted`, which means that we are trying to minimize the sum of integers that we deleted.

Each time we choose `a_k`, we delete `deleted[a_k] = count[a_{k-1}] * a_{k-1} + count[a_{k+1}] * a_{k+1}`, where `count[a_k]` denotes the number of `a_k`. So is it possible to greedily search for the minimal `deleted[a_k]` each time and delete them? I am not sure if this will lead to optimal solution.

### Official Solution

Use dynamic programming. For each integer `a_k`, we either choose it or delete it. So we can do dp from the largest integer that we have: 

1. Suppose `dp[k]` denotes the largest score that we can have with the array of integers given and delete all the integers larger than k. So for test case 

```
10
1 2 2 3 3 3 4 4 4 4 
```

`dp[2]` would denote the largest score that we can get from array `1 2 2`

2. `dp[k]` can be degraded to situation where either we choose `k` or not choose `k`. If we choose `k`, then `k-` would also be deleted, which would be `dp[k-2] + cnt[k] * k`. If we don't choose `k`, then it would be the same as `dp[k-1]`. So the dp formula:

`dp[k] = max({dp[k-2] + cnt[k] * k, dp[k-1]})`

```cpp
#include <iostream>
#include <cstring>
#include <algorithm>
using namespace std;
long long dp[100001] = {0};
int cnt[100001] = {0};
int n;
int max_num = 0;

int main()
{
    scanf("%d", &n);
    for (int i = 0; i < n; i++) {
        int a;
        scanf("%d", &a);
        cnt[a]++;
        max_num = max(a,max_num);
    }
    dp[1] = cnt[1];
    for (int i = 2; i <= max_num; i++) {
        dp[i] = max({dp[i-1], dp[i-2] + (long long)cnt[i] * i});
    }
    printf("%I64d", dp[max_num]);
    return 0;
}
```

### Thoughts

I didn't thought about dynamic programming ways to solve this problem. I guess the best way to come up with a dp solution is to degrade the question to easier scenarios. I think this question is actually a typical "choose or not" type of dp problem.

Also, still not sure whether my solution will work. I will think about it when I am better :D