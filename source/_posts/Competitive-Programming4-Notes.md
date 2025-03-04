---
title: '[CP4] - Competitive Programming 4 Notes'
date: 2025-03-01 14:59:01
categories: [CompetitiveProgramming, Notes, CP4]
tags: [Notes, CompetitiveProgramming, CP4]
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

# Data Structures

## Data Structures with standard libraries

### Linear Data Structures

1. Vector

| **Operation**            | **Time Complexity** | **Explanation** |
|--------------------------|--------------------|-----------------------------------------------------------|
| **Access Elements**      |                    | |
| `v[i]`                  | **O(1)**           | Direct index access is constant time. |
| `v.at(i)`               | **O(1)**           | Same as `v[i]`, but with bounds checking. |
| `v.front()` / `v.back()` | **O(1)**           | Accessing first or last element is constant time. |
| **Insertion & Deletion** |                    | |
| `push_back(x)`          | **O(1)** (amortized) | Adding an element to the end is usually constant time, but resizing can take O(n). |
| `pop_back()`            | **O(1)**           | Removes the last element in constant time. |
| `insert(pos, x)`        | **O(n)**           | Shifting elements to insert at `pos` takes linear time. |
| `erase(pos)`            | **O(n)**           | Removing an element requires shifting the remaining elements. |
| `erase(start, end)`     | **O(n)**           | Removing a range requires shifting elements after `end`. |
| `clear()`               | **O(n)**           | Frees memory by destructing elements. |
| **Size & Capacity**      |                    | |
| `size()`                | **O(1)**           | `std::vector` keeps track of its size. |
| `capacity()`            | **O(1)**           | Checking allocated memory is constant time. |
| `empty()`               | **O(1)**           | Checks whether the size is zero. |
| `resize(n)`             | **O(n)**           | Increasing size may require memory allocation and copying elements. |
| `shrink_to_fit()`       | **O(n)**           | Reduces capacity to fit size, may require reallocation. |
| **Searching & Sorting**  |                    | |
| `std::find(v.begin(), v.end(), x)` | **O(n)** | Linear search is slow for unsorted vectors. |
| `std::lower_bound(v.begin(), v.end(), x)` | **O(log n)** | Binary search in a sorted vector. |
| `std::upper_bound(v.begin(), v.end(), x)` | **O(log n)** | Finds the first element greater than `x`. |
| `std::sort(v.begin(), v.end())` | **O(n log n)** | Uses IntroSort (QuickSort + HeapSort + InsertionSort). |
| `std::reverse(v.begin(), v.end())` | **O(n)** | Swaps elements from both ends iteratively. |

2. Linked list

    - Usually not used in competitions

3. Stack

| **Operation**      | **Time Complexity** | **Explanation** |
|--------------------|--------------------|------------------------------------------------|
| `push(x)`         | **O(1)**           | Adds `x` to the top of the stack. |
| `pop()`           | **O(1)**           | Removes the top element. |
| `top()`           | **O(1)**           | Accesses the top element. |
| `size()`          | **O(1)**           | Returns the number of elements. |
| `empty()`         | **O(1)**           | Checks if the stack is empty. |

4. Queue

| **Operation**      | **Time Complexity** | **Explanation** |
|--------------------|--------------------|------------------------------------------------|
| `push(x)`         | **O(1)**           | Adds `x` to the back of the queue. |
| `pop()`           | **O(1)**           | Removes the front element. |
| `front()`         | **O(1)**           | Accesses the front element. |
| `back()`          | **O(1)**           | Accesses the back element. |
| `size()`          | **O(1)**           | Returns the number of elements. |
| `empty()`         | **O(1)**           | Checks if the queue is empty. |

## Non Linear Data Structures

### Binary Search Tree

Think of set and map as C++ built in implementation of Binary Search Tree, where every operation can be used in $O(log n)$ time. The only difference is that map stores a key-value pair and set stores only the key.

1. Set

| **Operation**        | **Time Complexity** | **Explanation** |
|----------------------|--------------------|------------------------------------------------|
| `s.insert(x)`       | **O(log n)**       | Insert `x` into the set (maintains order). |
| `s.erase(x)`        | **O(log n)**       | Removes `x` from the set. |
| `s.find(x)`         | **O(log n)**       | Returns an iterator to `x`, or `s.end()` if not found. |
| `s.count(x)`        | **O(log n)**       | Checks if `x` exists in the set (returns 0 or 1). |
| `s.lower_bound(x)`  | **O(log n)**       | Finds the first element **≥ `x`**. |
| `s.upper_bound(x)`  | **O(log n)**       | Finds the first element **> `x`**. |
| `s.begin()` / `s.end()` | **O(1)**       | Returns an iterator to the first/last element. |
| `s.size()`          | **O(1)**           | Returns the number of elements in the set. |

2. Map


| **Operation**        | **Time Complexity** | **Explanation** |
|----------------------|--------------------|------------------------------------------------|
| `m[key] = value;`   | **O(log n)**       | Insert or update `key → value`. |
| `m.insert({key, value})` | **O(log n)**  | Insert a new key-value pair. |
| `m.erase(key)`      | **O(log n)**       | Removes the key from the map. |
| `m.find(key)`       | **O(log n)**       | Returns an iterator to the key, or `m.end()` if not found. |
| `m.count(key)`      | **O(log n)**       | Checks if `key` exists (returns 0 or 1). |
| `m.lower_bound(key)` | **O(log n)**      | Finds the first key **≥ `key`**. |
| `m.upper_bound(key)` | **O(log n)**      | Finds the first key **> `key`**. |
| `m.begin()` / `m.end()` | **O(1)**       | Returns an iterator to the first/last key-value pair. |
| `m.size()`          | **O(1)**           | Returns the number of key-value pairs. |

### Heap

[Here](https://www.youtube.com/watch?v=t0Cq6tVNRBA) is a good video on heap. A heap is a complete binary tree where the root node is alawys larger than its children.


| **Operation**        | **Time Complexity** | **Explanation** |
|----------------------|--------------------|------------------------------------------------|
| `pq.push(x)`        | **O(log n)**       | Inserts `x` into the heap (maintains heap order). |
| `pq.pop()`          | **O(log n)**       | Removes the maximum (or minimum) element. |
| `pq.top()`          | **O(1)**           | Returns the highest priority element. |
| `pq.size()`         | **O(1)**           | Returns the number of elements in the queue. |
| `pq.empty()`        | **O(1)**           | Checks if the queue is empty. |
| **Heap Construction (`make_heap`)** | **O(n)** | Converts an array into a heap. |

For min-heap, we just use 

```cpp
priority_queue<int, vector<int>, greater<int>> minHeap;
```

### HashMap

Do not use this because C++ does not have a built in library for it.

# Study Plan

1. Week 1:

    - Day 1: Ch 1.1,1.2
    - Day 2: Ch 1.3, Ch 1.4
    - Day 3: Ch 2.1, Ch 2.2
