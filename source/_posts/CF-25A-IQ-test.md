---
title: '[CF] 25A - IQ test'
date: 2025-01-20 22:15:11
categories: [CompetitiveProgramming, CodeForces, ProblemSet]
tags: [Bruteforce,CPP]
code_block_shrink: false
---

My Very First CF problemset

<!--more-->

### My Solution

**Idea**: we don't need information from previous numbers, we only need three information: 

1. the common eveness `a`
2. the current number `b`
3. the index of the current number `num`

We also have a special case for when the first two numbers are different, in this situation we don't know which number is the more common one. Thus we only need to look at the 3rd number.

```cpp
#include<cstdio>
using namespace std;
int main() {
    int n, a, b, c, num = 2;
    scanf("%d", &n);
    scanf("%d%d", &a, &b);
    a = a % 2;
    b = b % 2;
    if (a == b) {
        while (num < n) {
            scanf("%d", &b);
            num++;
            if (b % 2 != a) {
                printf("%d", num);
                return 0;
            }
        }
    } else {
        scanf("%d", &c);
        if (c % 2 == a) {
            printf("2");
            return 0;
        }
        printf("1");
        return 0;
    }
    return 0;
}
```

### Official Solution

count the number of odd numbers and even numbers, store the last odd and last even, and do it bruteforcely.

### Thoughts

I guess the two solutions start from two different ways but they probably have a similar time and space achievement. 

This problem is my first problem in codeforces (since university), and it reminded me of how Olympiad was like :D