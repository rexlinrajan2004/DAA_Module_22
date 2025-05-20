# EX 4A DYNAMIC PROGRAMMING - 1
## DATE:
## AIM:
To find longest common subsequence using Dynamic Programming.



## Algorithm
1. Read two input strings u and v.
2. Create a 2D table c of size (len(u)+1) x (len(v)+1) initialized with -1, and set the last row and column to 0 as base cases.
3. Fill the table from bottom-right to top-left: if u[i] == v[j], set c[i][j] = 1 + c[i+1][j+1]; else set c[i][j] = max(c[i+1][j], c[i][j+1]).
4. To reconstruct the LCS, start from i = 0, j = 0, and follow the table values.
5. If characters match, print and move both pointers; if not, move in the direction of the larger value in the table.

## Program:
```
/*
Program to implement the longest common subsequence using Dynamic Programming
Developed by: REXLIN R
Register Number:  212222220034
*/
def lcs(u, v):
    """Return c where c[i][j] contains length of LCS of u[i:] and v[j:]."""
    c = [[-1]*(len(v) + 1) for _ in range(len(u) + 1)]
    for i in range(len(u) + 1):
        c[i][len(v)] = 0
    for j in range(len(v)):
        c[len(u)][j] = 0
 
    for i in range(len(u) - 1, -1, -1):
        for j in range(len(v) - 1, -1, -1):
            if u[i] == v[j]:
                c[i][j] = 1 + c[i + 1][j + 1]
            else:
                c[i][j] = max(c[i + 1][j], c[i][j + 1])
    return c
 
def print_lcs(u, v, c):
    """Print one LCS of u and v using table c."""
    i = j = 0
    while not (i == len(u) or j == len(v)):
        if u[i] == v[j]:
            print(u[i], end='')
            i += 1
            j += 1
        elif c[i][j + 1] > c[i + 1][j]:
            j += 1
        else:
            i += 1
 
u = input()
v = input()
c = lcs(u, v)
print_lcs(u, v, c)
```

## Output:

![image](https://github.com/user-attachments/assets/a2e762ef-61e4-449e-a813-6b14d64a7809)

## Result:
Thus the program was executed successfully for computing the length of longest common subsequence.
