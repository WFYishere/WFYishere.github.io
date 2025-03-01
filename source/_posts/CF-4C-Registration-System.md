---
title: '[CF] 4C - Registration System'
date: 2025-01-21 22:15:33
categories: [CompetitiveProgramming, CodeForces, ProblemSet]
tags: [HashMap, Bruteforce, CPP, C]
code_block_shrink: false
---

I learned some basics of C/C++, including scanf and cin, how to use hashMap in C, etc.

<!--more-->

### My Solution

Store the value in a hashMap, use the name as key and the number of times it appeared as value and just store+print.

**Idea**: 

```cpp
#include <iostream>
#include <unordered_map>
#include <cstring>
using namespace std;
int main() {
    unordered_map <string, int> hashMap;
    int n;
    char temp[50];
    scanf("%d", &n);
    while (n > 0) {
        scanf("%s", temp);
        string user_name(temp);
        if (hashMap.count(user_name) > 0) {
            hashMap[user_name] ++;
            printf("%s%d\n", user_name.c_str(), hashMap[user_name]);
        }
        else {
            hashMap[user_name] = 0;
            printf("OK\n");
        }
        n--;
    }
    return 0;
}
```

### Official Solution

pretty much the same

### Thoughts

I learned how to use C++ documentations to checkup functions

Also, a bit about how to use hashMap in C++

Also learned a bit about scanf and cin differences and how to mix C with C++ to write code (because scanf(C) is faster but C++ provides some good libraries.)