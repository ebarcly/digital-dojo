# Runtime Overview

When studying algorithms and data structures, you'll often come across the term **time complexity**. This concept is essential in computer science as it gives us insights into how long an algorithm will take to execute based on the size of the input.

### What is Time Complexity?

Time complexity refers to the amount of time an algorithm takes to run as a function of the input size. It provides an upper bound on the running time, offering a way to understand the worst-case scenario in terms of performance.

### Why is Time Complexity Important?

Consider having two solutions for sorting a list of numbers. While both solutions return the correct answer, one might take a minute to sort 1,000 numbers, while the other might only take a second. Naturally, you would choose the faster solution. Time complexity helps us predict performance differences without needing to run the algorithms with large inputs.

In analyzing time complexity, we often disregard constants. For example, both `O(2n)` and `O(5n)` are typically simplified to `O(n)` because they grow linearly with the input size. The goal is to identify the "family" of functions that most accurately describes the algorithm's growth in time.

### Big O Notation

Big O notation is used to describe an algorithm's time complexity. For instance, if an algorithm has a time complexity of `O(n)`, it means that, in the worst case, the algorithm's running time grows linearly with the input size `n`.

For example, a program that prints integers from `1` to `n` with a single for-loop would have a time complexity of `O(n)`. Even if the program prints numbers from `-100` to `5n`, the time complexity would remain `O(n)` because the time grows linearly with `n`.

In most cases, optimizing algorithms to account for minor constant factors is unnecessary. Basic runtime analysis often helps determine how efficient a solution is.

### Constraints and Operations

Coding platforms generally allow solutions to perform a maximum of **10-20 million operations**. This is useful information to consider when evaluating algorithm efficiency. Here's a video explaining how to analyze constraints in problem descriptions.

Now, let's break down the most common time complexities and how they relate to input sizes and algorithms:

---

## Time Complexity Categories

### `O(1)` - Constant Time

Operations that take constant time, regardless of input size. Examples include:

- Hashmap lookup
- Array access and updates
- Pushing and popping from a stack
- Finding or applying a mathematical formula

This is typically for inputs larger than `n > 10⁹`.

Example code (constant-time operations):

```python
a = 5
b = 7
c = 4
d = a + b + c + 153
```

### `O(log N)` - Logarithmic Time

Logarithmic time grows very slowly. For example, `log(1,000,000)` is around `20`. This is typical for algorithms like:

- Binary search
- Balanced binary search tree lookup
- Processing digits of a number

This is typically for input sizes greater than `n > 10⁸`.

Example code (halving each iteration):

```python
N = 100000000
while N > 0:
    # constant operation
    N //= 2
```

### `O(N)` - Linear Time

Linear time typically refers to iterating through a data structure a fixed number of times. Common cases include:

- Traversing arrays/linked lists
- Two-pointer algorithms
- Tree/graph traversal

Typically for `n ≤ 10⁶`.

Example code:

```python
for i in range(1, N + 1):
    # constant-time operation
```

### `O(K log N)` - Log-Linear Time with a Constant Factor `K`

This occurs when an operation is repeated `K` times, and each time the time complexity is logarithmic. Common use cases:

- Heap operations (push/pop) repeated `K` times
- Binary search `K` times

Typically for `n ≤ 10⁶`.

### `O(N log N)` - Log-Linear Time

Algorithms like sorting have an expected time complexity of `O(N log N)`. This is also typical for divide-and-conquer algorithms. For example:

- Sorting algorithms (e.g., merge sort, quicksort)
- Divide and conquer algorithms with a linear-time merge step

Typically for `n ≤ 10⁶`.

Example code:

```python
N = int(input())
ar = []
for i in range(N):
    m = int(input())
    ar.append(m)
ar.sort()  # O(N log N)
```

### `O(N²)` - Quadratic Time

Quadratic time arises from nested loops. Common use cases:

- Brute-force solutions
- Matrix traversal

Typically for `n ≤ 3000`.

Example code:

```python
for i in range(1, N + 1):
    for j in range(1, N + 1):
        # constant-time operation
```

### `O(2^N)` - Exponential Time

Exponential time grows rapidly and is typically found in recursive algorithms, such as combinatorial problems or backtracking. For example, Fibonacci recursion without memoization.

Typically for `n ≤ 20`.

Example code:

```python
def Fib(n):
    if n == 0 or n == 1:
        return 1
    return Fib(n - 1) + Fib(n - 2)
```

### `O(N!)` - Factorial Time

Factorial time grows incredibly fast and is typical for combinatorial problems, such as generating permutations. For example:

- Generating all permutations of a set

Typically for `n ≤ 12`.

---

## Amortized Time Complexity

Amortized time complexity is the average time per operation when expensive operations are performed occasionally. For instance, in a dynamic array, an `O(1)` append operation is usually performed, but occasionally an `O(N)` operation may be required to resize the array.

Example of amortized time complexity in a dynamic array append:

```python
size = None  # number of elements in array
capacity = None  # maximum capacity of array
arr = []

def append(x):
    if size == capacity:
        new_arr = [None] * (2 * capacity)
        capacity *= 2
        for i in range(size):
            new_arr[i] = arr[i]
        arr = new_arr
    arr[size] = x
    size += 1
```
---
