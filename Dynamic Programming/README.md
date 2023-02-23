# Dynamic Programming

Dynamic programming is an algorithmic technique that is widely used in competitive programming. It is a method for solving problems by breaking them down into smaller subproblems and solving each subproblem only once. The solutions to the subproblems are then combined to give the solution to the original problem. In this document, we will discuss the basics of dynamic programming and provide code snippets to explain its usage.

## Basic Concept

The basic concept of dynamic programming is to solve a problem by breaking it down into smaller subproblems and solving each subproblem only once. The solutions to the subproblems are then combined to give the solution to the original problem.

Dynamic programming is used when a problem has overlapping subproblems and optimal substructure. Overlapping subproblems refer to situations where the same subproblems need to be solved multiple times. Optimal substructure means that the solution to a problem can be obtained by combining the solutions to its subproblems.

### Fibonacci Series

The Fibonacci series is a classic example of a problem that can be solved using dynamic programming. The Fibonacci sequence is defined as follows:

``` Python
F(0) = 0
F(1) = 1
F(n) = F(n - 1) + F(n - 2) (for n > 1)

```

Here is an implementation of the Fibonacci series using dynamic programming:

``` Python
def fib(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        fib_arr = [0] * (n + 1)
        fib_arr[0] = 0
        fib_arr[1] = 1
        for i in range(2, n + 1):
            fib_arr[i] = fib_arr[i - 1] + fib_arr[i - 2]
        return fib_arr[n]

```

### Longest Common Subsequence

The longest common subsequence problem is another classic example of a problem that can be solved using dynamic programming. The problem is defined as follows:

Given two sequences, find the longest subsequence present in both of them.

Here is an implementation of the longest common subsequence problem using dynamic programming:

``` Python
def lcs(X, Y):
    m = len(X)
    n = len(Y)
    L = [[0 for x in range(n + 1)] for y in range(m + 1)]
    for i in range(m + 1):
        for j in range(n + 1):
            if i == 0 or j == 0:
                L[i][j] = 0
            elif X[i - 1] == Y[j - 1]:
                L[i][j] = L[i - 1][j - 1] + 1
            else:
                L[i][j] = max(L[i - 1][j], L[i][j - 1])
    return L[m][n]

```

Dynamic programming is a powerful technique that can be used to solve a wide range of problems in competitive programming. By breaking down problems into smaller subproblems and solving each subproblem only once, dynamic programming algorithms can be used to improve the efficiency and speed of code. The code snippets provided in this document serve as a starting point for understanding and implementing dynamic programming algorithms.


**And we are here to learn it in practice and get benefit of using it.**  
**Enjoy Dynamic Programming!**

## Dynamic Programming Topics Covered So Far
-   [Dynamic Programming: Introduction](https://github.com/AhmedGamal2212/Competitive-Programming-Sessions/tree/master/Dynamic%20Programming/Introduction)
-   [Dynamic Programming: Subsets, Counting, and Longest Increasing Subsequence (LIS)](https://github.com/AhmedGamal2212/Competitive-Programming-Sessions/tree/master/Dynamic%20Programming/Subsets%2C%20LIS%2C%20Counting)