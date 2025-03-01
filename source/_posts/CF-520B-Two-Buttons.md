---
title: '[CF] 520B - Two Buttons'
date: 2025-02-06 12:30:57
categories: 
- [CompetitiveProgramming, CodeForces, ProblemSet]
- [Unsolved]
tags: [Math, CPP, BFS]
code_block_shrink: false
---

Interesting problem with a much easier solution using mathematical methods.

<!--more-->

### My Solution

**Idea**: Use BFS to solve the problem. Imagine each node as the current displayed number `i`, the path from `n` to `i` is how we press the button to arrive at `i`. Using BFS, we are garuanteed that the first time that we see `m`, the path from `n` to `m` would be the shortest path.

```cpp
#include <iostream>
#include <unordered_map>
#include <cstring>
#include <cmath>
#include <queue>
using namespace std;
int MAX = 10000;
int main() {
    int n, m;
    scanf("%d%d", &n, &m);
    int cnt[MAX+1] = {0};
    queue<int> q;
    q.push(n);
    int curr = 0;
    cnt[n] = 0;
    while (curr != m && !q.empty()) {
        curr = q.front();
        q.pop();
        if (((curr - 1) > 0) && ((curr-1) <= MAX) && cnt[curr-1] == 0) {
            if ((curr - 1) == m) {
                printf("%d", cnt[curr] + 1);
                return 0;
            }
            cnt[curr - 1] = cnt[curr] + 1;
            q.push(curr - 1);
        }
        if (((curr * 2) > 0 ) && ((curr * 2) <= MAX) && cnt[curr*2] == 0) {
            if ((curr * 2) == m) {
                printf("%d", cnt[curr] + 1);
                return 0;
            }
            cnt[curr * 2] = cnt[curr] + 1;
            q.push(curr * 2);
        }
    }
    printf("%d", cnt[m]);
}
```

### Official Solution

Solution 1 is the solution that I have gave. The time complexity should be o(n).

Solution 2 is a more mathematical solution. This problem is equivalent to: how to reach from `m` to `n` given two operations `+1` and `/2`. 

Observe that the operation `+1 +1 /2` is equivalent to `/2 +1`, while the later takes less step. That means that consecutive `+1` would only appear at the end of the "optimal operation list", because consecutive `+1` should not appear before any `/2` (otherwise it would be replaced by `/2 +1`). 

This means that the optimal operation would look something like: some consecutive `/2`, some consecutive `+1 /2` followed by consecutive `+1`.

This means that the optimal solution is: when `m` is larger than `n`, we either `/2` if m is even, or `+1 /2` if m is odd. Until at some point `m` is smaller than `n`, then we keep `+1`. (See proof)

Furthermore, we can summarize that for given two kinds of operations `+b` and `/a`, where `b` and `a` are coprime, the only possible solution should be when `m` is larger than `n`, we `/a` whenerver `a` divides `m`, or `+b` until the current number divides `a`. When the current number is smaller than `n`, we keep `+b`.

*Proof: 

imagine `dp[i]` denotes the minimal number of times to press the button from `i` to `n`.

In this case, when `i` is larger than `n`:

1. `i` is not a multiple of `a`: `dp[i] = k + dp[i+kb]`. where `i+kb` is the minimal number that is a multiple of a(k > 0). I.e. In this situation, the only thing you can do is `+b`, until at some point we have the opportunity to choose`/a`, which would lead to the second scenario.

2. `i` is a multiple of `a`: In this case, `dp[i] = min{dp[i+b], dp[i/a]} + 1`. However, note that `dp[i+b]` goes back to the first scenario, which means that `dp[i+b] = a - 1 + dp[i+ab]`. Thus, `dp[i] = min{dp[i+ab] + a, dp[i/a] + 1}`. However, since `i` is larger than `n`, we know if we chose the `dp[i+ab] + a` part, at some point we have to divide by `a` to reach `n`. Suppose we decide to divide by `a` when we reach `i+kab`. That means, we reach `i/a+kb` by adding `b` `ka` times and dividing `a` 1 time. However, by the previous observation, we know that it would take less step if we divide a first and add `b` `k` times.  

When `i` is smaller than `n`: add b (?)


### Thoughts

Interesting problem. Hope I can prove it later.