# EX 4B DYNAMIC PROGRAMMING – 2
## DATE:
## AIM:
To find the longest string (or strings) that is a substring (or are substrings) of two strings..

## Algorithm
1. Read two strings X and Y, and store their lengths in variables m and n.
2. Create a 2D list lookup of size (m+1) x (n+1), initializing all values to 0.
3. Initialize two variables: maxLength = 0 and endingIndex = m to keep track of the longest match.
4. Use nested loops from i = 1 to m and j = 1 to n; if X[i-1] == Y[j-1], set lookup[i][j] = lookup[i-1][j-1] + 1.
5. If lookup[i][j] > maxLength, update maxLength and endingIndex.
6. After the loops, extract and print the substring from X[endingIndex - maxLength : endingIndex] as the longest common substring. 

## Program:
```
/*
Program to implement the longest common substring problem
Developed by: REXLIN R
Register Number:  212222220034
*/
def LCS(X, Y, m, n):
    maxLength = 0
    endingIndex = m
    lookup = [[0 for x in range(n + 1)] for y in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if X[i - 1] == Y[j - 1]:
                lookup[i][j] = lookup[i - 1][j - 1] + 1
                if lookup[i][j] > maxLength:
                    maxLength = lookup[i][j]
                    endingIndex = i
    return X[endingIndex - maxLength: endingIndex]

X = input()
Y = input()
m = len(X)
n = len(Y)
print('The longest common substring is', LCS(X, Y, m, n))
```

## Output:

![image](https://github.com/user-attachments/assets/71f7c9d6-cc65-45c1-bfa3-45b3b87d27c4)


## Result:
Thus the program was executed successfully for finding the longest common substring .
