---
title: '[CF] 230B - T-primes'
date: 2025-01-22 14:10:30
categories: [CompetitiveProgramming, CodeForces, ProblemSet]
tags: [Algorithms, CPP]
code_block_shrink: false
---

A simple problem on identifying prime numbers

<!--more-->

### My Solution

**Idea**: It's not hard to realize that we are looking for squared prime numbers. So for each number, we check whether it's a squared number, if yes, then we check whether the square root is a prime number

```cpp
#include <iostream>
#include <unordered_map>
#include <cstring>
#include <cmath>
using namespace std;
int main() {
    int n;
    scanf("%d", &n);
    long long x;
    while (n > 0) {
        scanf("%I64d", &x);
        long long m = floor(sqrt(x));
        if (m * m != x or x == 1) {
            printf("NO\n");
        } else {
            int s = floor(sqrt(m));
            bool is_prime = true;
            for (int i = 2; i <= s; i++) {
                if (m % i == 0) {
                    is_prime = false;
                    break;
                }
            }
            if (is_prime) {
                printf("YES\n");
            } else {
                printf("NO\n");
            }
        }
        n--;
    }
}
```

### Official Solution

Since range of x is `x <= 10^12`, square root of x is `sqrt(x) < 10^6` So we can try to precompute all possible prime numbers using [Sieve of Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes#:~:text=This%20algorithm%20produces%20all%20primes,as%20is%20usually%20the%20case.)

Store these prime numbers in a set and square it. Now for each input, we just need to check if it is in the set.

The code can be found [here](https://web.archive.org/web/20161225205232/http://pastie.org/4897166#10,13,15)

The time complexity is `O(sqrt(m) log log sqrt(m) + n * log(m_prime))`, where `m` is the upper bound of x, `m_prime` is the number of prime numbers within the 1 to `sqrt(m)`.

### Thoughts

Sometimes it's better to precompute stuff.