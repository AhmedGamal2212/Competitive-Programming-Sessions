## Longest Increasing Subsequence

The Longest Increasing Subsequence (LIS) is a classical problem in computer science and dynamic programming. Given an array of integers, we want to find the longest increasing subsequence within it. For example, given the array `[10, 9, 2, 5, 3, 7, 101, 18]`, the LIS is `[2, 3, 7, 101]` with length 4.

### Approach

To solve the LIS problem, we can use dynamic programming. We create an array `dp` of the same length as the input array, where `dp[i]` represents the length of the LIS ending at `nums[i]`. We initialize `dp[i]` to 1 for all `i`, since the LIS of a single element is just that element itself. We then iterate through the array, updating `dp[i]` for each element `nums[i]` by finding the maximum value of `dp[j] + 1` for all `j` such that `nums[j] < nums[i]`. This gives us the length of the LIS ending at `nums[i]`. Finally, we return the maximum value in `dp`.

### Code

``` Python
def lengthOfLIS(nums: List[int]) -> int:
    n = len(nums)
    dp = [1] * n
    for i in range(1, n):
        for j in range(i):
            if nums[j] < nums[i]:
                dp[i] = max(dp[i], dp[j] + 1)
    return max(dp)

```

***We Discussed more optimizations and applied it during the session***

## Counting

Counting problems are a common type of problem in computer science and dynamic programming. Given a set of objects, we want to count the number of ways we can select a subset of those objects that satisfy certain conditions.

### Approach

To solve counting problems, we can use dynamic programming. We create a table `dp` where `dp[i][j]` represents the number of ways to select a subset of the first `i` objects that satisfies the given condition(s) and has size `j`. We initialize `dp[i][0]` to 1 for all `i`, since the empty set is always a valid subset. We then iterate through the objects, updating `dp[i][j]` for each `i` and `j` by summing up the values of `dp[i-1][j-k]` for all `k` such that the subset of the first `i-1` objects has size `j-k` and satisfies the given condition(s) with the `i`-th object. This gives us the final answer, which is the sum of `dp[n][j]` for all `j` that satisfy the given condition(s).

### Code

``` Python
def countSubsets(objects: List[object], condition: Callable[[Set[object]], bool]) -> int:
    n = len(objects)
    dp = [[0] * (n+1) for _ in range(n+1)]
    for i in range(n+1):
        dp[i][0] = 1
    for i in range(1, n+1):
        for j in range(1, n+1):
            dp[i][j] = dp[i - 1][j]
            if condition(set(objects[:i])) and j >= 1:
                dp[i][j] += dp[i - 1][j - 1]
    ans = 0
    for j in range(n+1):
        if condition(set(objects[:n])) and j <= len(objects):
            ans += dp[n][j]
    return ans

```

# Knapsack Problem Variants

The Knapsack Problem is a classic problem in computer science and dynamic programming. Given a set of items, each with a weight and a value, and a knapsack with a maximum weight capacity, we want to find the most valuable subset of the items that can fit into the knapsack.

In this readme, we will explore some variants of the Knapsack Problem and how to solve them using dynamic programming.

## 0/1 Knapsack Problem

In the 0/1 Knapsack Problem, we are only allowed to take one instance of each item. The problem can be solved using dynamic programming. We create a table `dp` where `dp[i][j]` represents the maximum value that can be obtained using the first `i` items and with a knapsack of capacity `j`. We initialize `dp[i][0]` and `dp[0][j]` to 0 for all `i` and `j`, since we can't take any items if the knapsack has no capacity, and we can't get any value if there are no items. We then iterate through the items, updating `dp[i][j]` for each `i` and `j` by taking the maximum of `dp[i-1][j]` (if we don't take the `i`-th item) and `dp[i-1][j-w[i]] + v[i]` (if we do take the `i`-th item), where `w[i]` is the weight of the `i`-th item and `v[i]` is its value. The final answer is `dp[n][W]`, where `n` is the number of items and `W` is the maximum capacity of the knapsack.

### Code

``` Python
def knapsack01(W: int, wt: List[int], val: List[int], n: int) -> int:
    dp = [[0 for i in range(W + 1)] for j in range(n + 1)]
    for i in range(n + 1):
        for w in range(W + 1):
            if i == 0 or w == 0:
                dp[i][w] = 0
            elif wt[i - 1] <= w:
                dp[i][w] = max(val[i - 1] + dp[i - 1][w - wt[i - 1]], dp[i - 1][w])
            else:
                dp[i][w] = dp[i - 1][w]
    return dp[n][W]

```

## Other knapsack problem variants we didn't discuss in the session:

## Fractional Knapsack Problem (Greedy Problem)

In the Fractional Knapsack Problem, we are allowed to take fractional amounts of each item. The problem can be solved using a greedy algorithm. We first calculate the value per unit weight for each item, and then sort the items in non-increasing order of value per unit weight. We then take as much of each item as possible, starting with the item with the highest value per unit weight, until the knapsack is full.

### Code

``` Python
def fractional_knapsack(W: int, wt: List[int], val: List[int], n: int) -> float:
    items = list(zip(wt, val))
    items = sorted(items, key=lambda x: x[1] / x[0], reverse=True)
    max_val = 0
    for item in items:
        if W >= item[0]:
            max_val += item[1]
            W -= item[0]
        else:
            max_val += item[1] * (W / item[0])
            break
    return max_val

```

## Bounded Knapsack Problem

In the Bounded Knapsack Problem, we are allowed to take a limited number of instances of each item. The problem can be solved using dynamic programming. We create a table `dp` where `dp[i][j]` represents the maximum value that can be obtained using the first `i` items and with a knapsack of capacity `j`. We initialize `dp[i][0]` to 0 for all `i`, since we can't take any items if the knapsack has no capacity. We then iterate through each item, updating `dp[i][j]` for each `i` and `j` by taking the maximum of `dp[i-1][j-k*w[i]] + k*v[i]` for all `k` between 0 and the maximum number of instances of the `i`-th item, where `w[i]` is the weight of the `i`-th item and `v[i]` is its value. The final answer is `dp[n][W]`, where `n` is the number of items and `W` is the maximum capacity of the knapsack.

### Code

``` Python
def knapsack_bounded(W: int, wt: List[int], val: List[int], n: int, limit: List[int]) -> int:
    dp = [[0 for i in range(W + 1)] for j in range(n + 1)]
    for i in range(n + 1):
        for w in range(W + 1):
            if i == 0 or w == 0:
                dp[i][w] = 0
            else:
                dp[i][w] = dp[i - 1][w]
                for k in range(1, limit[i - 1]+1):
                    if wt[i - 1]*k <= w:
                        dp[i][w] = max(dp[i][w], dp[i - 1][w - k * wt[i - 1]] + k * val[i - 1])
    return dp[n][W]

```

## Multiple Knapsack Problem

In the Multiple Knapsack Problem, we have multiple knapsacks with different weight capacities, and we want to maximize the total value of the items we can take across all the knapsacks. The problem can be solved using dynamic programming. We create a table `dp` where `dp[i][j]` represents the maximum value that can be obtained using the first `i` items and with a total weight of `j` across all the knapsacks. We initialize `dp[i][0]` to 0 for all `i`, since we can't take any items if the total weight is 0. We then iterate through each item, updating `dp[i][j]` for each `i` and `j` by taking the maximum of `dp[i-1][j-k*w[i]] + k*v[i]` for all `k` between 0 and the maximum number of instances of the `i`-th item that can fit into the knapsacks with a total weight of `j`, where `w[i]` is the weight of the `i`-th item and `v[i]` is its value. The final answer is the maximum value in `dp[n][W]`, where `n` is the number of items and `W` is the total weight capacity of all the knapsacks.

### Code

``` Python
def multiple_knapsack(W: List[int], wt: List[int], val: List[int], n: int) -> int:
    dp = [[0 for i in range(sum(W) + 1)] for j in range(n+1)]
    for i in range(n+1):
        for w in range(sum(W)+1):
            if i == 0 or w == 0:
                dp[i][w] = 0
            else:
                dp[i][w] = dp[i - 1][w]
                for k in range(1, W[i-1]+1):
                    if wt[i - 1] * k <= w:
                        dp[i][w] = max(dp[i][w], dp[i - 1][w - k * wt[i - 1]] + k * val[i - 1])
    return dp[n][sum(W)]

```


## My Session @ ICPC SCU

- [Dynamic Programming: Subsets - Counting - LIS](https://www.youtube.com/watch?v=VLmp4bXaLto)

## Useful Materials

### Video Materials

- [Dynamic Programming - Subset Style (Dr. Mostafa Saad)](https://www.youtube.com/watch?v=vAqaki1BhS0&list=PLPt2dINI2MIattDutu7IOAMlUuLeN8k2p&index=3)
- [Dynamic Programming - Counting (Dr. Mostafa Saad)](https://www.youtube.com/watch?v=lE09Ss_Sy0A&list=PLPt2dINI2MIattDutu7IOAMlUuLeN8k2p&index=8)
- [Dynamic Programming | Set 3 (Longest Increasing Subsequence) | GeeksforGeeks](https://youtu.be/Ns4LCeeOFS4)
- [Longest Common Subsequence (LCS) - Recursion and Dynamic Programming (Abdul Bari)](https://youtu.be/sSno9rV8Rhg)


### Reading Materials

- [Dynamic Programming: Knapsack [Resources and Tutorial] (USACO)](https://usaco.guide/gold/knapsack?lang=cpp)
- [Dynamic Programming: Longest Increasing Subsequence (USACO)](https://usaco.guide/gold/lis?lang=cpp)
- [Longest Increasing Subsequence (CP-Algorithms)](https://cp-algorithms.com/sequences/longest_increasing_subsequence.html) ***Highly Recommended***

## Practice

- ***SOLVE AS MANY PROBLEMS AS YOU CAN FROM USACO***
- You can find here many useful problems:
    - [Assiut's Sheet I](https://vjudge.net/contest/463551)
    - [Assiut's Sheet II](https://vjudge.net/contest/463553)