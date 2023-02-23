# Recursion and Backtracking

Recursion and backtracking are important concepts in competitive programming. They are used to solve problems that can be broken down into smaller subproblems. In this document, we will discuss what recursion and backtracking are, their uses in competitive programming, and provide code snippets to illustrate their implementation.

## Recursion

Recursion is a technique where a function calls itself to solve a problem. It is particularly useful when dealing with problems that can be broken down into smaller subproblems. The function continues to call itself until a base case is reached, at which point the function returns the result.

### Example

```Python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)

```

In this example, the `factorial` function calls itself with a smaller `n` until `n` reaches 0, at which point the function returns 1.

## Backtracking

Backtracking is a technique used to find all possible solutions to a problem by incrementally building a solution and checking if it satisfies the problem's constraints. If a constraint is not satisfied, the algorithm backtracks and tries a different solution.

### Example

``` Python
def solve_sudoku(board):
    for i in range(9):
        for j in range(9):
            if board[i][j] == '.':
                for k in range(1, 10):
                    if is_valid(board, i, j, str(k)):
                        board[i][j] = str(k)
                        if solve_sudoku(board):
                            return True
                        else:
                            board[i][j] = '.'
                return False
    return True

```

In this example, we use backtracking to solve a Sudoku puzzle. The algorithm starts by iterating through the board and finding an empty cell. It then tries each number from 1 to 9 until a valid solution is found. If a solution is not found, the algorithm backtracks and tries a different number.

Recursion and backtracking are important techniques in competitive programming. They allow us to solve complex problems by breaking them down into smaller subproblems and finding all possible solutions. By understanding these concepts and knowing when to use them, we can write efficient and effective code.

**And we are here to learn them in practice and get benefit of using them.**  
**Enjoy Recursion and Backtracking!**

## My Session @ ICPC SCU

- [Recursion & Backtracking: Part 1](https://www.youtube.com/watch?v=msdBouUEs8w&t=0s&ab_channel=AhmedGamal)

- [Recursion & Backtracking: Part 2](https://www.youtube.com/watch?v=lBqumRAwEaQ&ab_channel=AhmedGamal)


## Useful Materials

### Video Materials

- [Recursion (Dr.Mostafa Saad)](https://www.youtube.com/watch?v=hyk46UmJPS4&list=PLPt2dINI2MIYmHYBSEdkdKMf_3nzFMveo&ab_channel=ArabicCompetitiveProgramming)

- [Backtracking (Dr. Mostafa Saad)](https://www.youtube.com/watch?v=hLXVhRzqq18&ab_channel=ArabicCompetitiveProgramming)

- [Divide & Conquer and Recurrence relations (Videos 18:29)(Abdul Bari)](https://www.youtube.com/playlist?list=PLDN4rrl48XKpZkf03iYFl-O29szjTrs_O)

- [Backtracking (Videos 63:67)(Abdul Bari)](https://www.youtube.com/playlist?list=PLDN4rrl48XKpZkf03iYFl-O29szjTrs_O)

### Reading Materials

- [Introduction to recursion (GeeksforGeeks)](https://www.geeksforgeeks.org/introduction-to-recursion-data-structure-and-algorithm-tutorials/)

- [Introduction to Backtracking (GeeksforGeeks)](https://www.geeksforgeeks.org/introduction-to-backtracking-data-structure-and-algorithm-tutorials/)

- [Time complexity of recursion (EnjoyAlgorithms)](https://www.enjoyalgorithms.com/blog/time-complexity-analysis-of-recursion-in-programming)

## Practice Problems

- [Recursion & Backtracking sheets (Assiut's Sheets)](https://codeforces.com/group/gA8A93jony/contests)