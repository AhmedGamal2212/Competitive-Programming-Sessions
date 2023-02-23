# Binary Search in Competitive Programming

Binary search is a fundamental algorithmic technique commonly used in competitive programming. It is a search algorithm that works on sorted arrays or lists by repeatedly dividing the search interval in half.

## How it works

Binary search works by comparing the target value to the middle element of the array. If the target value matches the middle element, the search is successful. Otherwise, the algorithm halves the search interval again and repeats the process until the target value is found or the search interval is empty.

This algorithm has a run-time complexity of O(log n), which is much faster than linear search (which has a run-time complexity of O(n)).

## Implementing Binary Search

Here's a simple implementation of binary search in Python:

``` Python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

```

## Applications of Binary Search

Binary search has many practical applications in computer science and is widely used in various fields. Some common applications of binary search include:

- Finding elements in a sorted list or array
- Finding the closest match in a sorted list or array
- Counting the number of occurrences of a target value in a sorted list or array


Binary search is an essential algorithmic technique that is commonly used in competitive programming. It is a fast and efficient way to search for target values in sorted arrays or lists. Understanding how binary search works and how to implement it is essential for any competitive programmer.

**And we are here to learn it in practice and get benefit of using it.**  
**Enjoy Binary Search!**

## My Session @ ICPC SCU

- [Binary Search](https://www.youtube.com/watch?v=K224kaUPVZc)

## Useful Materials

> I highly recommend starting with CodeForces EDU section

- [Binary Search (CodeForces EDU)](https://codeforces.com/edu/course/2/lesson/6/1)

### Video Materials

- [Search Techniques - Binary Search (Dr. Mostafa Saad)](https://www.youtube.com/watch?v=2G7RzlxTNPo&list=PLPt2dINI2MIZcJ3kADyFAOKOwzuvT-g7P)

- [Binary Search turtorial (Errichto)](https://www.youtube.com/watch?v=GU7DpgHINWQ)

### Reading Materials

- [Binary Search (TopCoder) **Highly Recommended**](https://www.topcoder.com/thrive/articles/Binary%20Search)

- [Binary Search (GeeksforGeeks)](https://www.geeksforgeeks.org/binary-search/)

- [Binary Search (programiz)](https://www.programiz.com/dsa/binary-search)


## Practice Problems

- [Binary Search sheet (ICPC SCU)](https://codeforces.com/group/KQlzWufN6x/contests)

- [Sqrt(X) (LeetCode)](https://leetcode.com/problems/sqrtx/)

- [Arranging Coins (LeetCode)](https://leetcode.com/problems/arranging-coins/)

- [Poisoned Dagger (CodeForces)](https://codeforces.com/problemset/problem/1613/C)

- [Sum of Cubes (CodeForces)](https://codeforces.com/problemset/problem/1490/C)

- [K-th Not Divisible by n (CodeForces)](https://codeforces.com/problemset/problem/1352/C)

- [Perfect Team (CodeForces)](https://codeforces.com/problemset/problem/1221/C)

- [Sport Mafia (CodeForces)](https://codeforces.com/problemset/problem/1195/B)
